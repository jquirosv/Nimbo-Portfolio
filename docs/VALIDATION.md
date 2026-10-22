# Validation and evidence

[← Nimbo Player](../README.md)

## Reviewed update — 0.8.1

- Review date: **October 21, 2026**.
- Source revision: `e0168be160c7bf4601d1b5db6c64ceca33ee41e2`.
- Branding revision: `b64117f0c7f998d514fcb6664ca0cf0c21431f76`.
- Displayed name: **Nimbo Player**; version **0.8.1**, Android version code **20**.

Source comparison confirms the updated Android name, onboarding and account copy, monthly recap branding, export names, and lyrics-request user agent. The existing sound halo keeps its paths and adds a central vinyl ring in the brand SVG and Android icon variants. Package, signing identity, persisted data, playback rules, and account API are preserved.

The source handoff records successful Kotlin formatting, the affected navigation test, and a debug build for the branding change. These recorded checks were not rerun for this documentation update. The release workflow is private run `39713271268`; the full-suite counts below remain attributed to the previously inspected 0.8.0 baseline.

## Inspected baseline — 0.8.0

- Baseline release: **0.8.0**.
- Review date: **October 21, 2026**.
- Private source revision: `9f515e65d27f564c7853c69cf8301995e929251a`.
- Private GitHub Actions run: `39560506032`, workflow **Checks**; Android and server jobs completed successfully.

The CI evidence was inspected through the authenticated repository API, the Android report artifact, and the server job log. These private reports are not public links; this case study summarizes their results without publishing operational logs. This documentation repository does not contain the application workflow or execute its tests.

## Inspected CI results

| Check | Result | Evidence scope |
| --- | --- | --- |
| Kotlin formatting | Passed | `:ktfmtCheck` |
| Android unit / Robolectric suite | **158 tests, 0 failures, 0 ignored** | `testDebugUnitTest` HTML report |
| Android lint, debug | 0 errors, 63 warnings | Debug lint XML |
| Android lint, release | 0 errors, 63 warnings | Release lint XML |
| Android debug build | Passed | `:app:assembleDebug` in successful Android job |
| Python lint and formatting | Passed | Ruff check and format check |
| Python tests | **12 tests, OK** | unittest output in successful server job |

The workflow uses Gradle tasks `:ktfmtCheck`, `:app:testDebugUnitTest`, `:app:lintDebug`, `:app:lintRelease`, and `:app:assembleDebug`. Passing lint does not mean a warning-free project.

## What the tests exercise

Source review found coverage around library persistence, playlist occurrences, lyrics lookup and concurrent saves, artwork behavior, listening aggregation and account ownership, backup revision handling, and recap rendering. Compose render fixtures exercise appearance, statistics, large text, and landscape layouts.

The source project's prior validation record also reports a successful Android 16 / API 36 instrumented recap-export test using synthetic audio and checking exported media and listening isolation. That recorded device run was **not rerun for this portfolio publication** and is separate from the inspected CI results above.

## Limits and further verification

- The inspected Android tests run on the host through unit/Robolectric infrastructure; they do not establish compatibility across physical devices.
- MP4 export depends on device codec capabilities. Storage permissions, SD cards, background scheduling, audio focus, and export need broader real-device checks.
- The gallery shows deterministic UI fixtures with fictional content, not production engagement or adoption.
- Lint warnings remain, and the evidence does not constitute a security audit, load test, store approval, or accessibility certification.
- No production account was created, production backup uploaded, or service redeployed for this publication.
