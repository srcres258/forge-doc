ForgeGradle 文档（中文翻译）
===========================

这里是[ForgeGradle]的官方文档，用于开发[MinecraftForge]以及使用MinecraftForge的模组的一个[Gradle]插件。

该文档 _仅_ 针对ForgeGradle编纂，**而不是一个Java、Groovy或Gradle教程**。

如果你愿意对文档做出贡献，请阅读[向文档做出贡献][contributing]。

添加该插件
---------

ForgeGradle使用Gradle 8；它可以使用`build.gradle`中的`plugins`块添加，方法是将以下信息添加到`settings.gradle`：

```gradle
// 在settings.gradle中
pluginManagement {
    repositories {
        // ...

        // 添加MinecraftForge maven
        maven { url = 'https://maven.minecraftforge.net/' }
    }
}

plugins {
    // 添加toolchain resolver
    id 'org.gradle.toolchains.foojay-resolver-convention' version '0.5.0'
}
```

```gradle
// 在build.gradle中
plugins {
    // 添加ForgeGradle插件
    id 'net.minecraftforge.gradle' version '[6.0,6.2)'

    // ...
}
```

[ForgeGradle]: https://github.com/MinecraftForge/ForgeGradle
[Gradle]: https://gradle.org/
[MinecraftForge]: https://github.com/MinecraftForge/MinecraftForge
[contributing]: ./contributing.md
