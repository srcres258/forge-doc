Pull Request准则
================

模组是在Forge之上构建的，但有些事情Forge不支持，这限制了模组的功能。
当模组开发者遇到类似的情况时，他们可以对Forge进行更改以支持它，并将该更改作为Pull Request提交到Github上。

为了充分利用你和Forge团队的时间，建议在准备Pull Request时遵循一些粗略的指导原则。在编写一个好的Pull Request时，以下几点是需要记住的最重要的方面。

到底什么是Forge？
----------------

在较高级别上，Forge是Minecraft之上的一个模组兼容性层。
早期的模组直接编辑了Minecraft的代码（就像现在的coremod一样），但当他们编辑相同的东西时，他们会遇到冲突。当一个模组以其他模组无法预料的方式改变行为时（就像现在的coremod一样），他们也遇到了问题，导致了神秘的问题和很多头痛。

通过使用Forge之类的东西，模组可以集中常见的更改并避免冲突。
Forge还包括通用模组功能的支持结构，如Capability、注册表和其他允许模组更好地协同工作的功能。

在编写一个好的Forge Pull Request时，你还必须知道Forge在较低级别上是什么。
Forge中有两种主要类型的代码：Minecraft补丁和Forge代码。

补丁
----

补丁是作为对Minecraft源代码的直接更改应用的，且致力于尽可能最小化。
每次Minecraft代码更改时，都需要仔细查看所有Forge补丁，并将其正确应用于新代码。
这意味着，改变很多事情的大型补丁很难维护，因此Forge的目标是避免这些补丁，并使补丁尽可能小。
除了确保代码有意义之外，对补丁的审查将侧重于最小化大小。

制作小补丁有很多策略，评论通常会指出更好的方法。
Forge补丁程序通常插入一行触发事件或代码挂钩，如果事件满足某些条件，就会影响之后的代码。
这允许大多数代码存在于补丁之外，从而使补丁保持小而简单。

有关创建补丁的更多详细信息，[请参阅GitHub wiki][patches]。

Forge代码
---------

除了补丁之外，Forge代码只是普通的Java代码。它可以是事件代码、兼容性功能，也可以是任何不直接编辑Minecraft代码的东西。
当Minecraft更新时，Forge代码必须像其他一切一样更新。然而，它要容易得多，因为它没有直接纠缠在Minecraft代码中。

因为这个代码是独立的，所以没有像补丁那样的大小限制。

除了确保代码有意义之外，评审（review）还将侧重于使代码干净：使用正确的格式和Java文档。

解释你自己
---------

所有Pull Request都需要回答一个问题：为什么这是必要的？
添加到Forge中的任何代码都需要维护，而更多的代码意味着更可能出现错误，因此添加代码需要有充分的理由。

一个常见的Pull Request问题是没有提供解释，或者给出了理论上如何使用Pull Request的神秘例子。
这只会延迟Pull Request过程。
对一般情况有一个明确的解释是好的，但也给出了一个具体的例子，说明你的模组如何需要这个Pull Request。

有时有更好的方法来做你想做的事情，或者一种完全不需要Pull Request的方法。在完全排除这些可能性之前，代码更改不能被接受。

证明它有效
---------

你提交给Forge的代码应该能完美地工作，这取决于你是否能说服评审人员。

最好的方法之一是在Forge中添加一个示例模组或JUnit测试，利用你的新代码并展示它的工作原理。

要使用示例模组设置和运行Forge环境，请参阅[这个指南][forgeenv]。

Forge中的突破性变化
------------------

Forge不能做出破坏依赖它的模组的更改。
这意味着Pull Request必须确保它们不会破坏与以前Forge版本的二进制兼容性。
破坏二进制兼容性的更改称为“突破性变化”。

关于这个有一些例外：

* Forge在新的Minecraft版本开始时接受突破性变化，因为Minecraft本身已经为模组开发者造成了突破性变化。
* 有时需要在该时间窗口之外进行紧急更改，但这种情况很少见，可能会给改装后的Minecraft社区中的每个人带来依赖性头痛。

在这些特殊时间之外，不接受具有突破性变化的Pull Request。它们必须适应以支持旧的行为，或者等待下一个Minecraft版本。

有耐心、有礼貌、有同情心
----------------------

在提交Pull Request时，你通常必须通过代码审查并进行多次更改，才能获得最佳的Pull Request。
请记住，代码审查并不是针对你的判断。代码中的错误不是针对个人的。没有人是完美的，这就是我们合作的原因。

消极也无济于事。威胁放弃你的Pull Request，转而编写一个coremod，只会让人们感到不安，并使修改后的生态系统变得更糟。
重要的是，在一起工作时，你要考虑到审查你的Pull Request的人的最佳意图，不要把事情看得太个人化。

审查（Review）
--------------

如果你尽最大努力理解Pull Request流程的缓慢和完美主义本质，我们也会尽最大努力了解你的观点。

在你的Pull Request经过审查并尽所有人所能进行清理后，它将被Lex标记为最终审查，Lex对项目中包含的内容拥有最终发言权。

[patches]: https://github.com/MinecraftForge/MinecraftForge/wiki/If-you-want-to-contribute-to-Forge#conventions-for-coding-patches-for-a-minecraft-class-javapatch
[forgeenv]: ./index.md
