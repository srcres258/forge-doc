向这篇文档做出贡献
==================

你可以通过在MinecraftForge的官方[GitHub]仓库提交PR来提交对这篇文档的贡献；若要对翻译文档提出修改，请访问[中文翻译GitHub仓库][GitHubTranslation]。

本文档的宗旨是明理达意。因此在提交贡献时，请解释它的工作原理，并将其拆分为合理的部分。
我们在其他地方有一个wiki，可以展示更全面的代码示例（未指明具体地点——译者注）。

我们的受众是任何一位想要了解如何通过Forge来构筑mod的人。

请不要试图将这篇文档转变为一篇关于Java开发的教程——后者意在教导人们一个Java类是如何工作的，以及一些Java的其他基本架构。

格式指南
--------

!!! 重要
    请使用**两个空格符**来进行缩进，而不是制表符。

标题应该以标准的标题样式对首字母进行大写或小写。例如，

* Guide For Contributing to This Documentation （中文：本文档贡献指南）
* Building and Testing Your Mod （中文：构建并测试你的Mod）

从本质上讲，除了不重要的单词外，所有单词都要大写。

拼写、语法和句法应遵循美式英语。此外，优先考虑使用用空格分割开的短语而不是缩写（例如“are not”而不是“aren't”）。

请使用等号和短划线，而不要使用“#”和“##”。对于h3及以下字体大小，“###”等也可以。此文件的源文件包含一个等号和短划线的示例。等号下划线创建h1文本，短划线下划线创建h2文本。

当引用代码块片段之外的字段和方法时，它们应该使用`#`分隔符（例如`ClassName#methodName`）。内部类应该使用`$`分隔符（例如`ClassName$InnerClassName`）。

JSON代码块片段应该使用`js`语法高亮显示。

所有链接都应在页面底部指定其URL。任何本文档的内部链接都应该通过其相对路径引用对应的页面。

警告（用`!!! <type>`表示）必须按照[该文档][admonition]所示进行设置；否则，它们最终可能会渲染不正确。

[GitHub]: https://github.com/MinecraftForge/Documentation
[GitHubTranslation]: https://github.com/srcres258/forge-doc
[admonition]: https://python-markdown.github.io/extensions/admonition/
