# Running in IDE

:::danger

This page is not suitable for non-developers.

:::

## IDE Selection

Recommended IDEs:

- **Android Studio (AS)**: Preferred IDE with better support for Android development
- **IntelliJ IDEA**: Alternative IDE with complete features, suitable for multiplatform development

## Running the Application

### Desktop

Create a new run configuration in the IDE using the following Gradle command:

```bash
desktopRun -DmainClass=top.kagg886.pmf.MainKt --quiet
```

### Android

Before running the Android application, you need to install the **Android plugin**.

After installation, you can run the Android application directly in the IDE.

### iOS

:::danger

iOS running can only be performed on macOS machines, and only M-chip Macs are supported. We do not and will not provide support for Intel Macs.

:::

Before running the iOS application, you need to install the **Kotlin MultiPlatform plugin**.

After installation, you can run the iOS application in the IDE.

## Notes

- Ensure JDK 17 is properly configured
- Desktop runtime requires proper run configuration setup
- Android requires Android SDK and related tools to be installed
- iOS requires Xcode and related toolchains to be installed
