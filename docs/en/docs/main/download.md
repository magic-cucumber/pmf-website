# Download Management

## Overview

The download management feature of PMF software has undergone significant improvements in version V1.6.6, providing a more convenient file management experience.

## Version Differences

### Before V1.6.6

In versions prior to V1.6.6:

- Images were saved to the APP's private directory
- Users had to manually click the "Save" button after download completion to access images in the external file system
- Users could not directly access downloaded files

### V1.6.6 to V1.8.0

From version V1.6.6 to V1.8.0, the download management feature has been significantly improved:

#### iOS
- **Save Location**: `My iPhone/Pixiv-MultiPlatform`
- **Authorization Required**: No additional authorization needed
- **Access Method**: Can be accessed directly through the Files app

#### Android
- **Save Location**: User-authorized folder
- **Authorization Required**: Need to authorize download path in settings page
- **Configuration**: Go to Settings → Download Settings → Select Download Folder

#### Desktop (Windows/Linux/macOS)
- **Save Location**: User-specified folder
- **Authorization Required**: Need to configure download path in settings page
- **Configuration**: Go to Settings → Download Settings → Select Download Folder

### V1.8.0 and Later

Starting from version V1.8.0, the download management feature has been further enhanced:

- **EPUB Export Integration**: EPUB export functionality has been moved to the download management system
- **Background Processing**: You can now exit the novel page while EPUB export is in progress
- **Unified Management**: All downloads and exports are now managed in one centralized location

## Configuring Download Path

### Android Configuration Steps

1. Open the PMF application
2. Go to Settings page
3. Find "Download Settings" option
4. Click "Select Download Folder"
5. Choose your desired folder for saving images in the system file picker
6. Confirm authorization

### Desktop Configuration Steps

1. Open the PMF application
2. Go to Settings page
3. Find "Download Settings" option
4. Click "Select Download Folder"
5. Choose your desired folder for saving images in the file selection dialog
6. Confirm selection

::: danger iOS Data Cleanup Reminder

iOS users can safely delete other non-image files found in the `My iPhone/Pixiv-MultiPlatform` directory, as these are data files from versions prior to V1.6.6 and will not affect the normal operation of the current version.

:::

## Frequently Asked Questions

### Q: Why can't I find my downloaded images?
A: Please ensure you are using V1.6.6 or a higher version, and have correctly configured the download path (Android and Desktop require configuration in settings).

### Q: Where are images saved on iOS?
A: On iOS, images are automatically saved to the `My iPhone/Pixiv-MultiPlatform` folder without requiring additional configuration.

### Q: How do I change the download path?
A: Android and Desktop users can reselect the download folder in "Download Settings" on the settings page. The download path on iOS is fixed and cannot be changed.
