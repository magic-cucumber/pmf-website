# Installation

## What systems is it compatible with?

Since version 1.6.0, Pixiv-MultiPlatform supports the following operating systems:

- Windows
- Linux
- macOS
- Android
- iOS

## How should I choose the installation package?

1. Click on the [download page](https://github.com/magic-cucumber/Pixiv-MultiPlatform/releases/latest)
2. Windows users, please jump to [Windows Installation](#windows-installation)
3. Linux users, please jump to [Linux Installation](#linux-installation)
4. macOS users, please jump to [macOS Installation](#macos-installation)
5. Android users, please jump to [Android Installation](#android-installation)

## Windows Installation

### Direct Extraction Method

1. Extract the files to a location of your choice
2. Click on `Pixiv-MultiPlatform.exe` to launch

### Using Windows Installer (.msi)

1. Download `windows.msi`

2. Double-click and select a suitable location for installation.

   :::warning

   By default, it will be installed to `C:\Program Files\Pixiv-MultiPlatform`. You can change the installation path if you prefer.

   :::

## Linux Installation

### Installation via Extraction

:::warning

pixiv-multiplatform strictly requires glibc>=2.39. You can run it on `ubuntu 24.04 LTS` and later versions

:::

:::warning

There is an [issue](https://github.com/magic-cucumber/Pixiv-MultiPlatform/issues/37) that proves the sqlite driver used by pixiv-multiplatform also requires a specific libunwind version. If you encounter the same problem, please feel free to leave a comment on this issue.

:::

Use the `tar` related commands to extract the archive file to a location of your choice

Grant executable permissions: `chmod +x ./Pixiv-MultiPlatform`

Double-click the file to launch.

### AUR Installation (Arch Linux only)

Currently, there are [third-party packages](https://aur.archlinux.org/packages?O=0&SeB=nd&K=pixiv-multiplatform&outdated=&SB=p&SO=d&PP=50&submit=Go) available for `AUR`. You can use the `yay -S` related commands to install. We won't elaborate further on this feature.

### Automated Installation Script

Since some people don't want to manually create desktop files, you can create a sh script in the same directory as the downloaded .tar.gz file:

```bash
#!/bin/bash

# Check if sudo is available
if ! sudo -v &>/dev/null; then
    echo "Sudo is not available, script will stop."
    exit 1
fi

# Check if the tar.gz file exists
if [ ! -f "linux.tar.gz" ]; then
    echo "linux.tar.gz file not found!"
    exit 1
fi

# Extract linux.tar.gz to /opt/Pixiv-MultiPlatform
echo "Extracting files to /opt/Pixiv-MultiPlatform..."
sudo tar -xzvf linux.tar.gz -C /opt/

# Create Pixiv-MultiPlatform.desktop file
echo "Creating the desktop entry..."
echo "[Desktop Entry]
Name=Pixiv-MultiPlatform
Comment=pixiv client on multiplatform
Exec=/opt/Pixiv-MultiPlatform/bin/Pixiv-MultiPlatform
Icon=/opt/Pixiv-MultiPlatform/lib/Pixiv-MultiPlatform.png
Terminal=false
Type=Application
Categories=Utility;" | sudo tee /usr/share/applications/Pixiv-MultiPlatform.desktop > /dev/null

# Give execution permission to the desktop file
echo "Giving execution permission to the desktop file..."
sudo chmod +x /usr/share/applications/Pixiv-MultiPlatform.desktop

# Run the Pixiv-MultiPlatform
echo "Running Pixiv-MultiPlatform..."
/opt/Pixiv-MultiPlatform/bin/Pixiv-MultiPlatform &
```

This script will:
1. Check for sudo privileges
2. Extract the application to `/opt/Pixiv-MultiPlatform`
3. Create a desktop entry for easy access
4. Launch the application automatically

## macOS Installation

1. Download the `.dmg` file
2. Double-click the file
3. Drag the icon to `Applications`
4. Launch the App

> ### Solution for when the dmg file cannot be installed on macOS
> 
> 1. Open
>    
>    ![image-20250130084342912](./install.assets/image-20250130084342912.png)
> 
> 2. Click through the following
>    
>    ![3](./install.assets/3.png)
> 
> 3. After entering your password, you can continue with the installation.

## Android Installation

1. Download the `android.apk` file to a location of your choice
   
   ::: info
   
   The default storage location should be in `Internal Storage/Downloads`
   :::

2. Open a file manager app on your phone (if you don't have one, please download a third-party file management tool like `MT Manager`), and locate the downloaded `android.apk`.

3. Tap to install, and pay attention to options like `Ignore Risk` during installation.

## iOS Installation

1. Download `iOS.ipa` to your computer.

2. Use a signing tool to sign it.

   ::: warning

   I have successfully installed and signed using `3uTools`.

   If you use `TrollStore` or other signing methods, you need to ensure **you have a MacBook** to capture the app's runtime crash logs, **otherwise I will be unable to help**

   :::

   ::: warning

   Since `1.7.4`, Pixiv-MultiPlatform's iOS support has been relaxed to iOS 16.4.

   Other **workflow** versions require iOS 18+

   :::

3. Install and open the application.

## Uninstallation

For Android, simply uninstall the app. For desktop versions, after deleting the folder, you need to remove residual files.

1. Windows residual files are in `C:\Users\username\.config\pmf`. Simply drag them to the recycle bin.
2. Linux residual files are in `~/.config/pmf`. Simply delete them.
3. macOS residual files are in `~/.config/pmf`. Simply delete them.
