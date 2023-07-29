ForgeGradle 文档（中文翻译）
===========================

这里是[ForgeGradle]的官方文档，用于开发[MinecraftForge]以及使用MinecraftForge的模组的一个[Gradle]插件。

该文档 _仅_ 针对ForgeGradle编纂，**而不是一个Java、Groovy或Gradle教程**。

如果你愿意对文档做出贡献，请阅读[向文档做出贡献][contributing]。

添加该插件
---------

ForgeGradle可以使用`plugins`块添加，方法是将MinecraftForge maven添加到可用的plugin repositories中：

```gradle
// 在settings.gradle中
pluginManagement {
    repositories {
        // ...

        // 添加MinecraftForge maven
        maven { url = 'https://maven.minecraftforge.net/' }
    }
}
```

```gradle
// 在build.gradle中
plugins {
    // 添加ForgeGradle插件
    id 'net.minecraftforge.gradle' version '5.1.+'

    // ...
}
```

[ForgeGradle]: https://github.com/MinecraftForge/ForgeGradle
[Gradle]: https://gradle.org/
[MinecraftForge]: https://github.com/MinecraftForge/MinecraftForge
[contributing]: ./contributing.md
