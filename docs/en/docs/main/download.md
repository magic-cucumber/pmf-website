# Download Management

## Overview

Download management supports image downloads and novel downloads, with advanced filtering capabilities.

::: danger

Versions between V1.6.6 - 1.8.0 do not support background EPUB download functionality.

:::

## Configure Download Path

1. Go to the Settings page
2. Find the "Download Settings" option
3. Click "Select Download Folder"
4. Choose the folder where you want to save images in the system file picker
5. Confirm authorization

## Save Location

| Platform                                 | Save Location                       | Authorization Requirements                     | Configuration Method / Access Method   |
| ---------------------------------------- | ----------------------------------- | ---------------------------------------------- | -------------------------------------- |
| **iOS**                                  | My iPhone/Pixiv-MultiPlatform       | No additional authorization required           | Accessible directly through Files app  |
| **Android**                              | User-authorized folder              | Need to authorize download path in Settings    | Visible in Gallery                     |
| **Desktop (Windows/Linux/macOS)**       | User-specified folder               | Need to configure download path in Settings    | Visible in File Manager                |

::: danger

iOS users can safely delete other non-image files seen in the `My iPhone/Pixiv-MultiPlatform` directory, as these are data files from before V1.6.6 and will not affect the normal use of the current version.

:::

### Advanced Search (V1.8.2+)

The advanced search feature allows you to filter and search downloaded content in download management.

#### Search Types

You can choose one of the following three search types:

- **All**: Search across all downloaded content (including illustrations and novels)
- **Illustrations**: Search only in downloaded illustrations
- **Novels**: Search only in downloaded novels

#### Keyword Search

Enter the content you want to search for in the keyword input box. The system will match based on your selected search type and search options.

#### Search Metadata

When the "Search Metadata" option is enabled, keywords can match not only filenames but also the information of the illustrations themselves, including:

- **Tags**: Match tags associated with illustrations
- **Illustration ID**: Match the unique identifier of illustrations
- **Other Metadata**: Match other intrinsic information of illustrations

::: tip

If the "Search Metadata" option is not enabled, search will only match filenames.

:::

## Download Management Features Before V1.6.6 (Archived)

::: danger

This version and earlier versions are not maintained, and related issues will be closed directly.

:::

- Images are saved to the app's private directory
- Must manually click the "Save" button after download completion to access images in the external file system
- Users cannot directly access downloaded files

