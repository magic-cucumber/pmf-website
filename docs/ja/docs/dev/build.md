# アプリケーションの構築 (v1.8.2以降)

:::warning

このチュートリアルは v1.8.2 のみを対象としています。以前のバージョンを構築したい場合、このチュートリアルには未解決の問題が含まれる可能性があり、自分で探索する必要があります。

:::

APP コードベースの成長と Rust コードの導入により、単一の `/gradlew` タスクでは APP の構築方法を完全に説明することはできません。このポストは特にこれを説明するために作成されました。

:::danger

このページは開発者向けではありません。

:::

## 前提条件

インストールする必須ツールチェーンは以下の通りです:

- **JDK 17**: コンパイルとビルド用
- **rustup**: Rust ツールチェーンマネージャー、Rust ターゲットプラットフォームのインストールと管理用

:::info

オプションのインストール: msvc、Rust ビルドツール選択用 (Windows プラットフォームで必須の場合があります)。

:::

:::tip

環境変数 `APP_VERSION_NAME` を設定することでバージョン番号を指定できます (オプション)：

```bash
export APP_VERSION_NAME=v1.8.2
```

:::

## デスクトップ プラットフォーム ビルド

:::tip オプション ステップ

AboutLibraries メタデータを生成します：

```bash
./gradlew exportLibraryDefinitions
```

:::

### ビルド コマンド

ビルド用に次のコマンドを使用します：

```bash
./gradlew packageReleaseDistributionForCurrentOS
```

:::tip Windows プラットフォーム

> v1.8.3 より前は、./gradlew light を使用してインストールプログラムパッケージを生成できます。このインストールにはショートカットなどの機能が含まれており、古い Compose プラグインバージョンではサポートされていませんでした。
> 
> 新しい Compose プラグインに移行したため、light ビルドコマンドは提供されなくなりました。

ビルド後、フラット化されたパッケージと MSI インストールプログラムが `composeApp/build/compose/binaries/main-release/app/` ディレクトリに生成されます。

:::

:::tip Linux プラットフォーム

ビルドの前に、システム依存関係をインストールする必要があります：

```bash
sudo apt update && sudo apt install libwayland-dev
```

ビルド後、フラット化されたパッケージが `composeApp/build/compose/binaries/main-release/app/` ディレクトリに生成されます。

:::

:::tip macOS プラットフォーム

macOS プラットフォームは特定のコマンドを使用して DMG インストールプログラムを生成する必要があります：

```bash
./gradlew packageReleaseDmg
```

ビルド後、DMG ファイルが `composeApp/build/compose/binaries/main-release/dmg/` ディレクトリに生成され、システムが自動的に開きます。

:::

## Android プラットフォーム ビルド

### 前提条件

Rust ターゲットプラットフォームをインストールします：

```bash
rustup target add aarch64-linux-android x86_64-linux-android
```

:::tip オプション ステップ

AboutLibraries メタデータを生成します：

```bash
./gradlew exportLibraryDefinitions -PaboutLibraries.exportVariant=release
```

:::

### ビルド コマンド

```bash
./gradlew assembleRelease
```

ビルド後、APK ファイルは `composeApp/build/outputs/apk/release/composeApp-release.apk` にあります。

:::warning

ビルド処理中に Rust 関連のエラーが発生した場合は、必要な Rust ターゲットプラットフォームが正しくインストールされていることを確認してください。インストール済みのターゲットプラットフォームは `rustup target list --installed` コマンドで確認できます。

:::

## iOS プラットフォーム ビルド

:::danger

iOS ビルドは macOS マシンでのみ実行でき、M チップ Mac のみがサポートされています。Intel Mac のサポートは提供されており、提供されません。

:::

### 前提条件

Rust ターゲットプラットフォームをインストールします：

```bash
rustup target add aarch64-apple-ios
```

:::tip オプション ステップ

AboutLibraries メタデータを生成します：

```bash
./gradlew exportLibraryDefinitions
```

:::

### ビルド コマンド

```bash
./gradlew buildReleaseIpa
```

:::tip

Xcode 16.2 以上が必要です。理論的には、バージョンを切り替えて環境変数を設定しなくてもビルドできます。

`xcode-select` で Xcode 16.2 を選択した後でもビルドが失敗する場合は、次の環境変数を追加してみてください：

```bash
sudo xcode-select -s /Applications/Xcode_16.2.app/Contents/Developer
export PATH=/Applications/Xcode_16.2.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS.sdk/usr/lib:$PATH
export LIBRARY_PATH="$LIBRARY_PATH:/Applications/Xcode_16.2.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS.sdk/usr/lib"
```

:::

ビルド後、IPA ファイルは `composeApp/build/archives/release/Pixiv-MultiPlatform.ipa` にあります。