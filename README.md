# Pranayama — Native Android app source

This is an Android Studio project for a native Kotlin implementation of the supplied Pranayama HTML app.

## What is implemented

- All 15 technique names and the corresponding technique instructions/cautions from the HTML reference.
- Adjustable inhale, inhale-hold, exhale and exhale-hold values (0–60 seconds).
- Adjustable target practice duration (30 seconds–60 minutes), cycle calculation and completion after whole cycles.
- Spoken phase labels and spoken second-by-second counting using Android Text-to-Speech.
- English voice selection, preferring an Indian-English voice where the Android TTS engine provides one.
- Optional phase-change bell and optional spoken technique introduction.
- Pause, resume, stop, completion and comfort feedback.
- Locally stored practice history, practice-day count, comfortable streak and optional +1 second exhalation suggestion after three comfortable saved sessions.
- Android foreground media-playback service and partial wake lock so the audio/counting service can continue while the screen is off.
- Persistent notification while a practice is running, with a Stop action.

## Build the APK

1. Install Android Studio (current stable) on Windows, macOS or Linux.
2. Open this folder (`PranayamaAndroid`) in Android Studio.
3. Allow Gradle sync and install Android SDK Platform 35 if prompted.
4. Select **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
5. The debug APK will be at `app/build/outputs/apk/debug/app-debug.apk`.
6. Copy the APK to the Android phone and install it. You may need to allow installation from that file manager/browser.

## Important Android settings

- Allow notifications for Pranayama so the ongoing practice notification is visible.
- Set the phone's battery setting for Pranayama to **Unrestricted** / **Don't optimize** if the manufacturer aggressively stops background apps. Menu wording varies by phone.
- Select/install an English (India) voice in Android Text-to-Speech settings if you want that voice. The app can only select voices supplied by the phone's TTS engine.
- Start the practice from the app before locking the phone. Android keeps the foreground media-playback service running and the partial wake lock keeps its timing thread awake.

## Limitations to validate on a real phone

- Android/OEM battery managers can still impose restrictions; test screen-off behaviour on the actual device.
- TTS voice quality and cadence depend on the installed speech engine and voice package. Unlike a pre-recorded audio track, TTS timing varies slightly by device.
- Pausing and resuming restarts the current phase from its beginning; it does not resume halfway through a spoken number.
- This first native build stores history on the device only. It does not sync between devices.

## Package details

- Application ID: `com.shiraschool.pranayama`
- Minimum Android: 8.0 (API 26)
- Target SDK: 35
- Version: 1.0
