# Submit Your Own Code

::: info Note
If you don't have a `Github account`, you can join our [Telegram group](https://t.me/+n_xsrc1Z590xNTY9)
:::

:::danger

This page is not suitable for non-developers.

:::

:::warning

This page assumes you have `Kotlin` and `Android` development environments on your computer.

:::

## General Steps

- Fork the branch
- Write code
- Commit code
- Send Pull Request

## Code Writing Guidelines

- `Kotlin` files are named using kebab-case

  > If a Kotlin file contains only one class/interface/object, use PascalCase for naming

- Try to avoid writing platform-specific functions unless necessary.

- When submitting a PR, please ensure your code can run on all targets. Some APIs can be found in `commonMain`, but may throw errors when compiled to specific platforms.

- Resource files use `SvgToCompose` for naming, and currently icons can be placed in `composeApp/src/commonMain/kotlin/top/magic-cucumber/pmf/ui/component/icon` and exposed in the `root` scope.

- Add comments in crucial places to aid understanding

## Pull Request Guidelines

- The title should concisely describe the main functionality of this PR; it's better not to combine multiple features in one PR.
- In the body of the PR, we should write the motivation for creating this PR and provide more detailed changes.
- Unfinished PRs can be converted to Draft.
- Merging will always use the `Squash and merge` method.
