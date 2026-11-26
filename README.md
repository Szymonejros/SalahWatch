# SalahWatch

Wear OS prayer companion app.

## Build APK with GitHub Actions

1. Upload the original `SalahWatch.zip` project archive to the repository root.
2. Commit it to `main`.
3. GitHub Actions automatically extracts the project, builds the debug APK, and uploads it as the `SalahWatch-debug-apk` artifact.
4. Open **Actions → Build SalahWatch APK → latest successful run → Artifacts** to download it.

You can also start a build manually from the workflow's **Run workflow** button after uploading the archive.

The build uses JDK 17, Gradle 8.9, and Android SDK 34. The generated APK is a debug build for Wear OS; it is not a Play Store release-signed package.
