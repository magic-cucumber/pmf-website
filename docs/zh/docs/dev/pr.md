# 提交自己的代码

::: info 温馨提示
若您没有`Github账号`，您可以加入我们的[TG交流群](https://t.me/+n_xsrc1Z590xNTY9)
:::

:::danger

本页面不适合非开发者阅读。

:::



:::warning

本页面默认您电脑中拥有`Kotlin`，`Android`开发环境。

:::



## 一般步骤

- Fork分支
- 编写代码
- 提交代码
- 发送Pull Request



## 代码编写细则

- `Kotlin`文件采用短划线命名法进行命名

  > 若Kotlin文件内只有一个类/接口/对象，则使用帕斯卡命名法进行命名

- 如非必要尽量不要编写平台函数。

- 提交pr时请确保您的代码可以在所有target中运行。有些API在`commonMain`里可以找到，但是在编译到特定平台时就会报错。

- 资源文件使用`SvgToCompose进行命名`，目前可以将图标放在`composeApp/src/commonMain/kotlin/top/magic-cucumber/pmf/ui/component/icon`中且暴露在`root`作用域。

- 在关键的地方加注释，便于理解

## Pull Request细则

- 标题需要简明扼要地写出这个pr主要干的功能，最好不要将多个功能合并在一个pr里。
- 在pr的正文中我们应该写出编写这个pr的动机以及更详细的改动。
- 未完成的pr可以转为Draft。
- 合并一律采用`压缩并合并`方式。
