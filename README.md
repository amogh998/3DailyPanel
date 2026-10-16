# 3DailyPanel Android wrapper (background lab reminder)

This Android project wraps the existing 3DailyPanel web UI in a native WebView and adds Android `AlarmManager` notifications. The reminder can fire while the app is closed and after a reboot, provided Android permits notifications and alarms.

## Build an APK in the cloud (no Android Studio required locally)
1. Create a new GitHub repository at https://github.com/new.
2. Upload the *contents* of this folder to the repository root (not the outer folder).
3. Open the repository's **Actions** tab and enable Actions if asked.
4. Select **Build 3DailyPanel APK** → **Run workflow**.
5. When it completes, open the run and download the `3DailyPanel-debug-apk` artifact.
6. Extract it; `app-debug.apk` is the APK to transfer to your Android phone and install. Android may ask you to allow installation from that source.

The workflow compiles a debug APK, suitable for personal testing. It is not a Play Store release/signed production build.

## Enable background reminders
- Open 3DailyPanel and allow notifications when Android asks.
- In IITGN Internship, set **Lab reminder time** and tap **Save reminder**.
- If Android asks for exact alarm permission, allow it in the system settings. If not granted, Android uses a less precise fallback that may be delayed.
- To change reminder time, save the new time in the app. Reboot restore is supported.

## What is native now
- Daily lab reminder scheduled with Android AlarmManager.
- Notification continues while the app is closed; schedule is restored after reboot.
- Existing app UI, daily tasks, internship logs, goals, revisions, mock tests and local data storage are included.

## Limitations and security
- This source workspace has no Android SDK/Gradle and no outbound network, so it cannot compile and attach the APK binary itself here. The included GitHub Actions workflow builds it in GitHub's hosted runner.
- The profile login is still local-only, not secure cloud authentication.
- WebView local storage is separate from Chrome's PWA storage, so the first APK launch starts with an empty local profile; use export/import only where data format is compatible.
- AI quiz needs internet and a user-provided OpenAI API key. Do not hardcode an API key into an APK. A secure backend is recommended for production.
- Android manufacturers may apply battery restrictions. If reminders are delayed, allow notifications and exact alarms for 3DailyPanel and disable battery optimization for it.
