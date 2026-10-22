# Engineering decisions

[← Nimbo Player](../README.md)

## 1. Give playlist entries their own identity

The same track can appear more than once in a playlist. Treating the song ID as the entry identity makes reorder, remove, and playback operations target the wrong occurrence.

Nimbo Player operates on playlist occurrences and positions. A repeated track can be removed or moved independently, and playback starts from the selected occurrence. Undo restores the corresponding operation rather than searching for the first matching song.

## 2. Update rows without destroying relationships

SQLite `REPLACE` can delete the existing song row before inserting a new one. With cascading foreign keys, a metadata edit can consequently erase playlist or artwork relationships.

Existing rows are updated in place. Common artwork and per-theme variants are stored separately, with the effective artwork reflected on the song. Disabling variants freezes the visible choice while preserving saved variants for reactivation.

## 3. Measure listening rather than wall-clock gaps

Listening time uses a monotonic clock and active playback intervals. Pauses do not accumulate time; seeking does not create a listening interval for the skipped section. Play accreditation and elapsed listening are separate concerns, so brief listening can contribute actual time without becoming a completed play.

Version 0.8.0 separates listening ownership by account. Legacy history is claimed once; later account changes preserve independent histories instead of merging them.

## 4. Make retries mean the same operation

A response can disappear after the server has accepted a backup. Rebuilding that retry from newer statistics would give one pending revision different meanings on consecutive requests.

Nimbo Player persists the payload before sending and retries that same payload until acknowledgement. The pending state is scoped by owner, device, month, and generation. Revision conflicts are reconciled, and stale generations are rejected. Session epochs are checked around asynchronous responses to prevent a previous account's result from entering the current session.

Daily scheduling includes the open month. Android may defer background work, so daily scheduling is supplemented by foreground attempts and does not promise an exact upload time.

## 5. Keep recap audio outside listening analytics

Recaps may preview music while the user's main queue already exists. Reusing the main playback service would alter the queue and risk recording preview audio as a new listen.

The recap soundtrack is independent. Closing a recap resumes the original entry only when it was previously playing and remains unchanged. Frozen snapshots and thumbnails preserve the monthly story even when the live library changes. The same artboard produces the UI, PNG frames, and MP4 composition.

Media3 playback, effects, and Transformer stay on the same 1.8.0 version. Export relies on supported device codecs; physical-device coverage remains a separate validation task.

## 6. Make lyrics assistance explicit

Lookup uses title, artist, album, and duration to find candidates, then lets the user review them. Web-copy assistance is limited to the active lyrics window. It does not read the clipboard silently in the background or when the window opens, and does not expose a JavaScript bridge or WebView file/content access.

The lyrics editor retains the destination song ID and expected fields. Saving updates the current row only when those fields still match, protecting concurrent edits from an old search result. Tests inject transport and invented lyrics instead of depending on live requests.

## 7. Treat accessibility as part of the layout

Player and appearance renders exercise large text and landscape layouts. Reduced motion starts recap stories in manual-advance mode; recap playback also responds to lifecycle pauses. These are implemented adaptations, with broader assistive-technology and device checks still requiring manual validation.
