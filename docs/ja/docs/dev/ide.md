# IDE で実行

:::danger

このページは開発者向けではありません。

:::

## IDE 選択

推奨される IDE：

- **Android Studio (AS)**: Android 開発に優れたサポートが得られる推奨 IDE
- **IntelliJ IDEA**: マルチプラットフォーム開発に適した機能が完全な代替 IDE

## アプリケーション実行

### デスクトップ

IDE で次の Gradle コマンドを使用して新しい実行構成を作成します：

```bash
desktopRun -DmainClass=top.kagg886.pmf.MainKt --quiet
```

### Android

Android アプリケーションを実行する前に、**Android プラグイン** をインストールする必要があります。

インストール後、IDE で Android アプリケーションを直接実行できます。

### iOS

:::danger

iOS 実行は macOS マシンでのみ実行でき、M チップ Mac のみがサポートされています。Intel Mac のサポートは提供されており、提供されません。

:::

iOS アプリケーションを実行する前に、**Kotlin MultiPlatform プラグイン** をインストールする必要があります。

インストール後、IDE で iOS アプリケーションを実行できます。

## 注意

- JDK 17 が正しく構成されていることを確認してください
- デスクトップ実行には適切な実行構成設定が必要です
- Android には Android SDK と関連ツールをインストールする必要があります
- iOS には Xcode と関連ツールチェーンをインストールする必要があります