# Build Pranayama APK in the cloud (no Android Studio)

This project includes a GitHub Actions workflow that builds the Android debug APK on GitHub's hosted Linux runner. You do **not** need to install Android Studio or Java on your computer.

## One-time setup

1. Sign in to GitHub or create a free account at https://github.com.
2. Create a new **private** repository, for example `pranayama-android`.
3. On the new repository page choose **Add file → Upload files**.
4. Upload the *contents* of this project folder, including the hidden `.github` folder. If your browser does not show hidden folders, upload the ZIP using GitHub's web interface only if it extracts the folder structure; otherwise use GitHub's web editor to create `.github/workflows/build-apk.yml` and paste the workflow file contents.
5. Commit the files to the `main` branch.
6. Open the repository's **Actions** tab. Select **Build Pranayama APK** on the left and click **Run workflow** if it has not started automatically.
7. Wait for the workflow to finish with a green check mark. Open that run, scroll to **Artifacts**, and download **Pranayama-debug-APK**.
8. Extract the downloaded artifact ZIP. It contains `app-debug.apk`.
9. Transfer `app-debug.apk` to your OnePlus 12R and tap it to install. If Android asks, allow your file manager/browser to install unknown apps. Only install APKs built from this repository that you control.

## What the workflow does

- Uses Java 17, Gradle 8.9, Android SDK Platform 35 and Build Tools 35.0.0.
- Runs `gradle clean assembleDebug`.
- Publishes `app-debug.apk` as a downloadable workflow artifact for 14 days.

## Device target

The app's current configuration has `minSdk 26` and `targetSdk 35`. It should install on Android 16 / OxygenOS 16, including the OnePlus 12R, subject to real-device testing. This is a debug build, not a Play Store release or a cryptographically signed production release.

## Important testing note

The project source has not been compiled or tested on a physical OnePlus 12R yet. A successful cloud build confirms compilation, not that every feature behaves correctly on the phone. Test a short session first, lock the screen, and confirm that spoken cues and bells continue. Android/OxygenOS battery controls may need to be set to **Unrestricted** for Pranayama. Do not rely on the app for medically prescribed breathing therapy until its timing and behaviour have been independently checked.
