# GSC Audio Speed Controller (Android source project)

An offline Android audio player for stenography practice. Select one audio file, enter its original WPM, then switch playback target between 60 and 160 WPM in 5-WPM increments without creating separate audio files.

## Features
- Audio picker using Android's document picker (MP3, WAV, M4A and other supported formats)
- Copies imported audio into the app's private storage and remembers it and the WPM settings between launches
- 60–160 WPM buttons in 5-WPM increments
- Calculates playback rate as `target WPM / original WPM`
- Uses Media3 ExoPlayer `PlaybackParameters(speed, 1.0f)` to change tempo while keeping pitch at 1.0
- Play/pause and seek bar
- No network permission and no server dependency

## Build the APK
1. Install **Android Studio** on a Windows, Mac or Linux computer.
2. Open Android Studio and choose **Open**; select this project folder (`GSC_Audio_Speed_Controller`).
3. Allow Gradle sync. Use JDK 17 (Android Studio's embedded JDK is suitable).
4. Install Android SDK Platform 35 when prompted.
5. Connect an Android phone with USB debugging enabled, or use an emulator.
6. For a test install, choose **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
7. Android Studio will show the APK location, normally `app/build/outputs/apk/debug/app-debug.apk`.
8. For a distributable signed APK, choose **Build > Generate Signed Bundle / APK > APK** and create a keystore. Keep the keystore safe.

## Important notes
- This is the Android Studio source project, not a precompiled APK. An Android SDK/Gradle build environment is not available in this workspace, so an APK has not been compiled or device-tested here.
- When you import an audio file, the app copies it into its own private storage. You can then move or delete the original source file; the imported copy remains in the app until app data is cleared or the app is uninstalled.
- Actual WPM must be entered by the user. The app does not automatically measure speech WPM from an audio file.
- Pitch preservation is requested through Media3's playback parameters (`pitch = 1.0`). Very extreme speed changes may still sound less natural depending on the recording/device.
- Branding currently uses the GSC name and maroon theme. A supplied logo image can be added later as the launcher/app header logo.

## Playback rate example
For an original recording of 84 WPM:
- 80 WPM => 80 / 84 = 0.9524x (95.24%)
- 90 WPM => 90 / 84 = 1.0714x (107.14%)
