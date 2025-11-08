# 构建应用程序(自V1.8.2)

:::warning

该教程仅供 v1.8.2 版本的构建，若要构建更早版本，此教程可能会含有未解决的问题，此时请自行探索。

:::

随着APP代码库的增长以及rust代码的引入，单一的`/gradlew`任务已经无法完整地说明如何构建这个APP，特开此贴以进行说明。

:::danger

本页面不适合非开发者阅读。

:::

## 前置要求

必须安装的工具链如下：

- **JDK 17**：用于编译和构建
- **rustup**：Rust 工具链管理器，用于安装和管理 Rust 目标平台

:::info

可选安装：msvc，用于 Rust 的构建工具选择（Windows 平台可能需要）。

:::

:::tip

可以通过设置环境变量 `APP_VERSION_NAME` 来指定版本号（可选）：

```bash
export APP_VERSION_NAME=v1.8.2
```

:::

## 桌面平台构建

:::tip 可选步骤

生成 AboutLibraries 元数据：

```bash
./gradlew exportLibraryDefinitions
```

:::

### 构建命令

统一使用以下命令进行构建：

```bash
./gradlew packageReleaseDistributionForCurrentOS
```

:::tip Windows 平台

Windows 用户可以使用 `./gradlew light` 生成经过改善的 MSI 安装包：

```bash
./gradlew light
```

构建完成后，会在 `composeApp/build/compose/binaries/main-release/app/` 目录下生成 flatten 包体和 MSI 安装包。

:::

:::tip Linux 平台

在构建前，需要安装系统依赖：

```bash
sudo apt update && sudo apt install libwayland-dev
```

构建完成后，会在 `composeApp/build/compose/binaries/main-release/app/` 目录下生成 flatten 包体。

:::

:::tip macOS 平台

macOS 平台需要使用专门的命令生成 DMG 安装包：

```bash
./gradlew packageReleaseDmg
```

构建完成后，会在 `composeApp/build/compose/binaries/main-release/dmg/` 目录下生成 DMG 文件，系统会自动打开该文件。

:::

## Android 平台构建

### 前置步骤

安装 Rust 目标平台：

```bash
rustup target add aarch64-linux-android x86_64-linux-android
```

:::tip 可选步骤

生成 AboutLibraries 元数据：

```bash
./gradlew exportLibraryDefinitions -PaboutLibraries.exportVariant=release
```

:::

### 构建命令

```bash
./gradlew assembleRelease
```

构建完成后，APK 文件位于 `composeApp/build/outputs/apk/release/composeApp-release.apk`。

:::warning

如果构建过程中出现 Rust 相关错误，请确保已正确安装所需的 Rust 目标平台。可以通过 `rustup target list --installed` 命令查看已安装的目标平台。

:::

## iOS 平台构建

:::danger

iOS 构建只能在 macOS 机器上进行，且只支持 M 芯片。我们不会也未来不会为 Intel Mac 提供支持。

:::

### 前置步骤

安装 Rust 目标平台：

```bash
rustup target add aarch64-apple-ios
```

:::tip 可选步骤

生成 AboutLibraries 元数据：

```bash
./gradlew exportLibraryDefinitions
```

:::

### 构建命令

```bash
./gradlew buildReleaseIpa
```

:::tip

最低需要 Xcode 16.2 版本，理论上不执行切换版本和设置环境变量也能构建。

如果在 `xcode-select` 选择了 Xcode 16.2 后仍然构建失败，试着添加以下环境变量：

```bash
sudo xcode-select -s /Applications/Xcode_16.2.app/Contents/Developer
export PATH=/Applications/Xcode_16.2.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS.sdk/usr/lib:$PATH
export LIBRARY_PATH="$LIBRARY_PATH:/Applications/Xcode_16.2.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS.sdk/usr/lib"
```

:::

构建完成后，IPA 文件位于 `composeApp/build/archives/release/Pixiv-MultiPlatform.ipa`。
