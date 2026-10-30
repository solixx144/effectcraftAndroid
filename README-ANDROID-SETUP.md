# EffectCraft Android starter (unofficial community port)

This starter adds an Android WebView shell and GitHub Actions workflows to the EffectCraft source tree.
It does **not** yet provide native Android parity. The app currently loads the project's existing
WebAssembly build from GitHub Pages. GPU/WebGPU availability, browser storage, audio, imports and
exports must be validated on the target Android device before treating the port as usable.

## Add these files to the root of `solixx144/effectcraftAndroid`

Copy the contents of this folder into the root of your fork, preserving paths. Do not replace the
upstream source files. Commit to the `main` branch.

## Enable Pages

In the GitHub repository open **Settings → Pages** and set **Build and deployment → Source** to
**GitHub Actions**.

## Build the web app

Open **Actions → Build and deploy EffectCraft Web → Run workflow**. Wait for both jobs to finish.
The Android shell expects this URL:

`https://solixx144.github.io/effectcraftAndroid/`

If the page fails to load, verify that Pages deployed successfully and that the repository name and
username match the URL in `MainActivity.kt`.

## Build the APK

Open **Actions → Build EffectCraft Android APK → Run workflow**. When it finishes, open the run's
**Artifacts** section and download `effectcraft-android-debug-apk`. Extract it and install
`app-debug.apk` on the tablet.

## Current limitations

- This is an initial WebView wrapper, not a completed native Android port.
- WebGPU may be unavailable in Android System WebView on some device/software versions. EffectCraft
  documents a WebGL2 fallback, but the app's full feature set still needs device testing.
- Browser storage and file chooser/download integration are preliminary.
- The APK requires network access to load the hosted web app. The web app itself may cache resources
  after first load, but offline startup is not guaranteed by this wrapper.
- Do not publish or distribute this unofficial build as an official EffectCraft release.

Keep the upstream MIT/Apache license and attribution notices intact.
