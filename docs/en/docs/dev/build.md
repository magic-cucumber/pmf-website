# Building the Application (since V1.8.2)

:::warning

This tutorial is only for building v1.8.2. If you want to build earlier versions, this tutorial may contain unresolved issues, and you should explore on your own.

:::

With the growth of the APP codebase and the introduction of Rust code, a single `/gradlew` task can no longer fully explain how to build this APP. This post is created specifically to provide explanation.

:::danger

This page is not suitable for non-developers.

:::

## Prerequisites

The must-install toolchains are as follows:

- **JDK 17**: For compilation and building
- **rustup**: Rust toolchain manager, for installing and managing Rust target platforms

:::info

Optional installation: msvc, used for Rust build tool selection (may be required on Windows platform).

:::

:::tip

You can specify the version number by setting the environment variable `APP_VERSION_NAME` (optional):

```bash
export APP_VERSION_NAME=v1.8.2
```

:::

## Desktop Platform Building

:::tip Optional Step

Generate AboutLibraries metadata:

```bash
./gradlew exportLibraryDefinitions
```

:::

### Build Command

Use the following command for building:

```bash
./gradlew packageReleaseDistributionForCurrentOS
```

:::tip Windows Platform

Windows users can use `./gradlew light` to generate an improved MSI installer:

```bash
./gradlew light
```

After building, the flatten package and MSI installer will be generated in the `composeApp/build/compose/binaries/main-release/app/` directory.

:::

:::tip Linux Platform

Before building, you need to install system dependencies:

```bash
sudo apt update && sudo apt install libwayland-dev
```

After building, the flatten package will be generated in the `composeApp/build/compose/binaries/main-release/app/` directory.

:::

:::tip macOS Platform

macOS platform needs to use a specific command to generate DMG installer:

```bash
./gradlew packageReleaseDmg
```

After building, the DMG file will be generated in the `composeApp/build/compose/binaries/main-release/dmg/` directory, and the system will automatically open it.

:::

## Android Platform Building

### Prerequisites

Install Rust target platforms:

```bash
rustup target add aarch64-linux-android x86_64-linux-android
```

:::tip Optional Step

Generate AboutLibraries metadata:

```bash
./gradlew exportLibraryDefinitions -PaboutLibraries.exportVariant=release
```

:::

### Build Command

```bash
./gradlew assembleRelease
```

After building, the APK file is located at `composeApp/build/outputs/apk/release/composeApp-release.apk`.

:::warning

If Rust-related errors occur during the build process, please ensure that the required Rust target platforms are correctly installed. You can check installed target platforms using the `rustup target list --installed` command.

:::

## iOS Platform Building

:::danger

iOS building can only be performed on macOS machines, and only M-chip Macs are supported. We do not and will not provide support for Intel Macs.

:::

### Prerequisites

Install Rust target platform:

```bash
rustup target add aarch64-apple-ios
```

:::tip Optional Step

Generate AboutLibraries metadata:

```bash
./gradlew exportLibraryDefinitions
```

:::

### Build Command

```bash
./gradlew buildReleaseIpa
```

:::tip

Minimum Xcode 16.2 is required. Theoretically, you can build without switching versions and setting environment variables.

If the build still fails after selecting Xcode 16.2 with `xcode-select`, try adding the following environment variables:

```bash
sudo xcode-select -s /Applications/Xcode_16.2.app/Contents/Developer
export PATH=/Applications/Xcode_16.2.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS.sdk/usr/lib:$PATH
export LIBRARY_PATH="$LIBRARY_PATH:/Applications/Xcode_16.2.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS.sdk/usr/lib"
```

:::

After building, the IPA file is located at `composeApp/build/archives/release/Pixiv-MultiPlatform.ipa`.
