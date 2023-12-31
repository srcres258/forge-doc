# 调试分析器

Minecraft提供了一个调试分析器，它提供系统数据、当前游戏设置、JVM数据、存档数据和tick信息，以查找耗时的代码。考虑到像`TickEvent`和计时`BlockEntities`这样的事情，这对想要找到滞后源的模组开发者和服务器所有者来说非常有用。

## 使用调试分析器

调试分析器使用起来非常简单。它需要调试绑定键`F3 + L`来启动分析器。10秒后，它将自动停止；但是，可以通过再次按绑定键提前停止。

!!! 注意
    当然，你只能分析实际到达的代码路径。要分析的实体和方块实体必须存在于存档中才能显示在结果中。

停止调试器后，它将在运行目录中的`debug/profiling`子目录中创建一个新的zip。
文件名的格式为日期和时间`yyyy-mm-dd_hh_mi_ss-WorldName-VersionNumber.zip`

## 阅读一个分析结果

在每个端位的文件夹（`client`和`server`）中，你会发现一个包含结果数据的`profiling.txt`”文件。在顶部，它首先告诉它运行了多长时间（以毫秒为单位）以及在这段时间内运行了多少tick。

在下面，你将找到与以下片段类似的信息：
```
[00] levels - 96.70%/96.70%
[01] |   Level Name - 99.76%/96.47%
[02] |   |   tick - 99.31%/95.81%
[03] |   |   |   entities - 47.72%/45.72%
[04] |   |   |   |   regular - 98.32%/44.95%
[04] |   |   |   |   blockEntities - 0.90%/0.41%
[05] |   |   |   |   |   unspecified - 64.26%/0.26%
[05] |   |   |   |   |   minecraft:furnace - 33.35%/0.14%
[05] |   |   |   |   |   minecraft:chest - 2.39%/0.01%
```
以下是每个部分的含义的小解释

| [02]                     | tick                  | 99.31%       | 95.81%       |
| :----------------------- | :---------------------- | :----------- | :----------- |
| 该部分的深度              | 该部分的名称           | 所花费的时间相对于其父项的百分比。对于层级0，它是一tick所用时间的百分比。对于层级1，它是其父层所用时间的百分比。 | 第二个百分比告诉整个tick所花的时间。

## 分析你自己的代码

调试分析器具有对`Entity`和`BlockEntity`的基本支持。如果你想分析其他内容，你可能需要手动创建你的部分，如下所示：
```java
ProfilerFiller#push(yourSectionName : String);
// 你想分析的代码
ProfilerFiller#pop();
```
你可以从`Level`、`MinecraftServer`或`Minecraft`实例获取`ProfilerFiller`实例。
现在，你只需要在结果文件中搜索你的部分的名称。
