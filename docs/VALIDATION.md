# Validation and evidence

[← Nimbo](../README.md)

## Reviewed source

- Release described: **0.8.0**.
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
