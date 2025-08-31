# Novels

## 1. Browsing

The novel browsing page looks like this:

| PC                                                           | Android                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![image-20250321112730835](./novel.assets/image-20250321112730835.png) | ![image-20250321113116613](./novel.assets/image-20250321113116613.png) |

- Click the pen icon in the upper right corner to display the novel details sidebar, including cover image, author information, title, and other information
- Click the heart to bookmark, click the tag content to search by tags
- Click comments to view the comment section

## 2. Novel Preview Settings

![image-20250321113228674](./novel.assets/image-20250321113228674.png)

### Auto Formatting (Enabled by Default)

Auto formatting can help you screen out some textual differences in novels, providing a more comfortable reading experience.

Here's a comparison:

| Auto Formatting Enabled                                      | Auto Formatting Disabled                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![image-20250321112730835](./novel.assets/image-20250321112730835.png) | ![image-20250321113902225](./novel.assets/image-20250321113902225.png) |

> You can adjust the font size of the novel through the `Body Size` setting. This will also adjust the line height accordingly.

:::details What does Auto Formatting do?

1. Indents the first line by 2 character widths

   > Due to a Compose bug, this can only be implemented by adding spaces to achieve indent.

2. Uses regular expressions to remove excess blank lines

3. Completely removes spaces before and after each paragraph

If you want to know the specific code implementation of auto formatting, please refer to [rich-text.kt](https://github.com/kagg886/Pixiv-MultiPlatform/blob/483bf913a2cb98a3df0056468e0f77a12d5b58fa/composeApp/src/commonMain/kotlin/top/kagg886/pmf/ui/util/rich-text.kt#L234)

:::

### Filter Long TAG Novels

You've probably seen this type of content with excessive tags in search results:
![image-20250321114328989](./novel.assets/image-20250321114328989.png)

This feature can approximately block such articles by checking the length of the TAGs.

:::warning

There is a tendency that preview-type articles also have this trend of using extremely long TAGs for traffic.

If this feature affects your user experience, please turn it off (it's off by default).

:::

### Filter Extremely Short Novels

You've probably seen these kinds of ~~articles~~ with no substance yet taking up space when searching:

![image-20250321114653345](./novel.assets/image-20250321114653345.png)

This feature can block such content by checking the total word count of these articles, making the search results show the content you want rather than these contact exchanges or role-playing messages.

> Of course, this feature can also be used to only view articles that exceed a specified word count.

### Fetching Series When Fetching Novel

When enabled, if a novel belongs to a series, a navigation bar will be displayed at the bottom of the novel, allowing you to quickly navigate to the previous/next chapter.

If you disable this feature, the navigation bar will never appear, even for novels that are part of a series.

:::tip

This feature is particularly useful for reading multi-chapter novels or series, as it provides seamless navigation between chapters without having to go to the novel details page → novel series page to select one by one.

:::