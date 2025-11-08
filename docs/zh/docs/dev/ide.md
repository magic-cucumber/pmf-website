# 在 IDE 中运行

:::danger

该页面不适合非开发者阅读。

:::

## IDE 的选择

推荐使用以下 IDE：

- **Android Studio (AS)**：首选 IDE，对 Android 开发有更好的支持
- **IntelliJ IDEA**：次选 IDE，功能完整，适合多平台开发

## 运行程序

### 桌面端

在 IDE 中新建运行任务，使用以下 Gradle 命令：

```bash
desktopRun -DmainClass=top.kagg886.pmf.MainKt --quiet
```

### Android 端

运行 Android 端程序前，需要安装 **Android 插件**。

安装完成后，可以直接在 IDE 中运行 Android 应用。

### iOS 端

:::danger

iOS 运行只能在 macOS 平台进行，且只支持 M 芯片。我们不会也未来不会为 Intel Mac 提供支持。

:::

运行 iOS 端程序前，需要安装 **Kotlin MultiPlatform 插件**。

安装完成后，可以在 IDE 中运行 iOS 应用。

## 注意事项

- 确保已正确配置 JDK 17
- 桌面端运行时需要正确配置运行任务
- Android 端需要安装 Android SDK 和相关工具
- iOS 端需要安装 Xcode 和相关工具链
