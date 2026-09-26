# Audashi — Android APK build project

This is a ready-to-build Android (Capacitor) wrapper around the Audashi game.
It can't be compiled inside this chat (no Android SDK here), but it builds
automatically for free using GitHub Actions — no Android Studio required.

## Option A: Build in the cloud with GitHub Actions (recommended, free)

1. Create a new **empty** repository on GitHub (e.g. `audashi-app`).
2. Upload everything in this folder to that repo (drag-and-drop on
   github.com works, or `git init && git add . && git commit -m init && git push`).
3. Go to the repo's **Actions** tab. A workflow called "Build Android APK"
   will run automatically (or click **Run workflow** if it doesn't).
4. When it finishes (a few minutes), open the finished run and download the
   **audashi-debug-apk** artifact — that's a .zip containing `app-debug.apk`.
5. Send that APK to your phone (email, Drive, USB, etc.), tap it to install.
   Android will warn about "unknown sources" the first time — that's normal
   for an app not from the Play Store; allow it for this install.

## Option B: Build locally with Android Studio

1. Install [Android Studio](https://developer.android.com/studio).
2. Open the `android/` folder in this project as an existing project.
3. Let Gradle sync, then Build ▸ Build Bundle(s)/APK(s) ▸ Build APK(s).
4. The APK appears under `android/app/build/outputs/apk/debug/`.

## Notes

- This builds a **debug** APK, which installs and plays fine but isn't
  signed for the Play Store. If you want a signed release build, Android
  Studio's Build ▸ Generate Signed Bundle/APK wizard handles that.
- The game itself lives in `www/` as a plain static web build — if you want
  to tweak the game logic later, edit the source and rebuild `www/` with
  Vite, then run `npx cap sync android` again before rebuilding the APK.
