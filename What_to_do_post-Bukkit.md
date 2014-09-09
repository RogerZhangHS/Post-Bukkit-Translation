我们正在对于我们的之后的未来进行一项公众调查，以让我们决定我们之后的何去何从，在目前这个情况下，你可以加入IRC频道 irc.esper.net 6667 #nextstep。
这个文档受许多从#nextstep频道中来的具有共识的人们而编辑。在加入讨论之前请先请仔细阅读整个文档，因为你所提出的意见可能早已被提出。
发生了什么？

  **请务必帮助我们完成这份调查！（需要翻墙）：http://bit.ly/1qnO8Gm**
  _你可以点击这里查看调查的结果：https://docs.google.com/forms/d/1lQ0eXyfaEHJPutFPAtNQk2XQteqHSKT4OJXWGFNfVio/viewanalytics_

##话题是什么？
  * **净室软件开发？**
    * 不。为什么？在我们所知的范围内并没有任何Minecraft的Java接口支持净室软件开发。所以，我们完全逃不掉EULA的限制。
    * 不。太多开发者们已经深入研究了Minecraft源代码太多了，完全算不上净室软件开发的范畴了。

  * **在目前的MOD平台上构建？**
    * FORGE。为什么？早已经建立的玩家社群，避免了从头开始的困境。

  * **用什么API？**
    * CANARY或SPOUT。详情请看调查问卷结果。

##目录：
  * 发生了什么？
  * 目录
  * 最受欢迎的意见
  * 所有可用的意见
  * 备注
  * 问题
  * 要求
  * 引用
  * API比较

##热门方案
当前看来比较好的解决方案是写一个新的抽象API（无需1：1的参照Minecraft对象）。和Bukkit有点像，但是是基于Forge或者Glowstone。
  * Forge是一个已经有很多Mod而且当前非常流行的服务器/客户端API。并且Forge平台当前已经有非常大的社区了。
  * 但是因为Forge并非“抽象API”。一旦在Mojang在新老两个版本之间做出太多大改动，Forge将无法跨版本使用。因此如果新的API基于Forge，这个问题必须解决掉。
  * 如果让Forge模组使用“抽象API”将可以像Bukkit使用NMS一样而达到Forge版本无关性。这样的话模组开发人员就有了更加强大工具来开发模组。
    * 这个说法是错误的。使用抽象层就像Bukkit实际API一样而且不直接操作NMS。事实上并没有明确的说“抽象”，所以和“使用NMS”来说没有可比性。Forge是使用NMS的，任何顶层的抽象将被更多的束缚（很严重的束缚）。
  * Glowstone 是一个独立的MC服务器实现。和Bukkit.Forge.Spigot.Canary不同，它不依托于Mojang的源码。
    * 有人建议无论社区同意哪一种API，API都应当建立在Glowstone之上。
    * 当前Glowstone已经引入了Bukkit API原因是Glowstone并未直接使用Minecraft专利的源码。

  * 单纯的使用一个独立的MC Server重实现并不适用于所有人。因为它可能无法获取最新的MC功能。这对于好多人来说是个问题，因为他们单纯的想建立一个普通的创造服或者生存服。
  * 可以预见到的是，假设当项目启动之后某些在MC上依然还是预览版的功能在Spout就已经可用。但是这完全取决于开发者的速度和功能实现的难度。
 * 如果去写一个新的API的话，有些人认为使用Spout（不是Spoutcraft）或者Canary的API可以重用代码，这样可以节省很多的工作量。但是这并不意味着无论如何都将吸收他们大量的核心代码。


##所有可用的意见
注：某些建议是由其他服务端的开发者所撰写的，由此，可能会有一些偏见。
  * 1.换至Bukkit的竞争对手
    * a.换至Canary平台
      * i.Canary包含官方的 minecraft_server ，因此会违反服务条款（重要）
      * ii.玩家社群并不大
      * iii.使用BSD 3-Clause License
      * iv.人们会想将Canary和Forge一起使用，Canary Lib可以被用作未来的类似于Cauldron服务端的东西。（Canary团队正在关注）
      * v.他们的网站上文档详细
      * vi.可以使用抽象层，就像Bukkit具有的那样。包含许多Bukkit本身具有的功能，同时也有许多被需要的API功能
        * NBT仅仅是一小部分
      * vii.团队建立时间较长
        * 尽管如此，但团队人数较少，并不能十分迅速的开发
          * viii.一些在Bukkit平台上十分受欢迎的插件也同样兼容Canary
    * b.换至 Minecraft Forge （并内置一个API）
      * i.较大的玩家社群，被许多MOD所使用（加分）
        * 与Bukkit有着不同的思想，Forge通过使用API尝试暴露尽可能多的NMS代码。但是Bukkit将所有东西都隐藏在抽象层后面。
      * ii.需要一个经过修改的客户端才能使用，但根据LexManos，可能在1.8后就不再需要了
      * iii.每过一个版本，特定种类的MOD就不能够使用（重要）
        * Forge现在和今后都不会提供抽象层，因此哪怕是一些很小的Minecraft更新，MOD作者也需要更新他的作品。
        * srgname OBF帮助。但并没有像Bukkit里面那样的write-once-ignore之类的东西。
        * 当然这些仅限于大型的计划，一些小型的MOD仅仅使用Forge API的接口
      * iv.在Bukkit和Spigot上面的性能表现欠佳
        * 可以被'修复'，但需要时间和人手
        * a.我们能尝试使用Spigot的优化嘛？
          * i.可以，但需要书面许可
        * b.我们能使用现在已有的优化程序嘛？
          * i.首先我们需要清楚这些优化程序能不能让服务端的性能表现像当前的服务端一样。要不然这完全没有意义
          * ii.有可能性，但我们也需要提前询问。并且我们要搞清楚我们所做的事儿有多少侵略性。
      * v.对于开发者的易用性差
        * 有一些（或很多）开发者认为Forge难以使用
        * 缺少正确的PR(Post/Request)处理系统
          * a.如果社群足够大，我们或许可以向LexManos**施加压力**？
        * 尽管可以被修复，但它缺少足够的文档
          * a.玩家们自行制作的教程可以在论坛上查看。但如果有官方的教程还是最好的
      * vi.缺少与Bukkit相同的功能，但可以被修复
  * 2.切换到一个独立的净室开发的服务端
    * a.换至 Glowstone
      * i.这个计划已存在很久，并且也与目前版本同步
                缺少极大量的功能，比如说W-Gen
      * ii.基本上已经与Minecraft的新功能脱节了，因为它是完全独立的从零开始的Minecraft服务端（重要）
      * iii.可以使用Bukkit API
      * iv.包含Bukkit API。可能会有许可方面的问题（重要）
      * v.与Forge Mod不兼容（重要）
    * b.换至MCServer
      * i.使用C++编写
      * ii.可能十分有效率（加分）
      * iii.除非Java提供绑定，目前所有现有的Java代码必须在Lua下重写（重要）
      * iv.多协议支持，可以从Minecraft 1.2直接支持到Minecraft1.7.10（加分）
      * v.与Forge Mod不兼容（重要）
    * c.换至Craft.net
      * i.使用C#编写
      * ii.与Forge Mod不兼容（重要）
    * d.换至Spout
      * i.当前的开发工作不在进行中，而是在由一个在Github上的flow-engine流仓库下"继续开发"中。Spout或者flow-engine其中之一必须被Fork。
      * ii.与当前最新的Minecraft新版本功能已经完全脱节。原因是Spout是使用与Minecraft独立的功能重写。（重要）
      * iii.即用，因为Spout只是单纯的引擎（客户端/服务端）,你需要原版插件即可使用。
      * iv.为了兼容而设计的BukkitBridge模块（重要）有一些性能上的问题 BukkitBridge所以需要慎用。
      * v.不同于其他的API首先需要解决客户端的问题，Spout的客户端代码得去掉一部分。甚至需要合并一些原版服务端代码才能完成一个MinecraftServer的功能。
      * vi.无法与Forge mods兼容（重要）
  * 3.将Bukkit API引入到现有的实现中（Forge，Canary）
    * d.BukkitForge
      * i.在Forge的基础之上。
      * ii.曾经名噪一时，但是最终在1.5.2被抛弃（重要）
      * iii.代码中依然保留着Bukkit的API-可能会受到许可的约束等问题。（重要）
  * 4.启动一个新项目并使用Bukkit API或者新的API
    * a.（_否决的_）迁移至TridentSDK
      * i.虽然只是一个最近才兴起的小项目，但这同样也是一个方案。
      * ii._坏主意！_ - Chunkr. 这个项目太不成熟了！
    * b.我们自己来做！
      * i.繁重如山的工作量（重要）
      * ii.应该部分的/很大程度上兼容现在已有的API
      * iii.使用什么许可最合适？GNU？ GPL？ LGPL？ MIT？
      * iv.这样可以使我们更加自由的决定工作方向
      * v.重新排序现有的API至新的API的可能性？90+%？兼容性？（反馈）
      * vi.需要集成Forge API？
      * vii.是否对社区完全透明开放？
  * 5.Runtime patch with current Bukkit and Craftbukkit code (i.e. Mojang’s code is never distributed in the same binary as the GPL code -- rather, it is combined when the user runs the server)
    * a.Very dangerous in regards to Bukkit’s licensing situation (MAJOR)
    * b.Can use Bukkit API（加分）
      * i.Bukkit API is Mojang owned, may not be a plus
  * 6.Install patch with current Bukkit and Craftbukkit code  (i.e. Mojang’s code is never distributed in the same binary as the GPL code -- rather, it is combined via a simple installer, which allows users to build their own server, using our, and their own patches)
    * a.Less dangerous, but still very dangerous in regards to Bukkit’s licensing situation  (MAJOR).
      * i.We can ‘ditch’ most if not all bukkit code, and use our own implementation, the default server already has most parts we need, all we need to add is a good API, which isn’t a whole lot of work, but certainly less work than writing a entire server from scratch, opinions?
        * Not sure whether it’s just a good idea, maybe keep the bukkit API and reimplement craftbukkit?
    * b.Possibly ‘more’ legal than distributing the minecraft-server.jar
    * c.Can use Bukkit API（加分）
  * 7.Wait until Mojang releases the API
    * a.May be a very long wait, potentially years (we waited 2, and are still waiting) (MAJOR)
    * b.It will be an step up from Bukkit in what you can do, but it will not compare to Forge, et. al. which permit client modding because you will not be able to execute your own code on the client 
    * c.Possibly the lamest api we’ve ever seen, looking at the current possibility’s using command blocks, e.g. totally written, and made to be used on realms. Likely won’t compare to the extensible changes possible with current APIs.
      * i.Considering what Mojang’s been doing recently, could it be a ploy to force people on realms (conspiracy theory)
  * 8.Implement a plugin API that acts as a wrapper around the Minecraft server
    * a.May even work on snapshots
    * b.Likely very fast to update (MAJOR)
    * c.Very limited as to what can be done (MAJOR)
      * i.Can only do what can be done by modifying network packets or reusing what can be done with command blocks 

#备注
 * With nearly everything at this point in the Minecraft community being written in Java, a Java based server would probably gain the most support.
 * Using the current minecraft-server.jar is the easiest way to go, distributing patches which patch the server-code to insert ‘our’ code, allows experienced users to use java reflection to change base code, and use things we haven’t implemented in the API yet.
 * Vanilla clients need to be able to connect to it. Quite simply, if we’re looking for a post-Bukkit option, it’ll have to be this way. (MAJOR)

#问题
  * 1.Are we going to stick to ONE protocol, or are we planning to be MULTI protocol.
    * a.Only applies if we’re going to write our own software.
    * b.Really doesn’t matter, as we can simply update the protocol as MC updates come out. Mojang will probably keep updating the protocol a tiny smudge in areas, making multi protocol nearly impossible anyways.
    * c.The current status quo is that Bukkit/MC isn’t multiprotocol, so not too many people will really care for this I imagine
  * 2.Ownership, how will this be ‘run’ who will oversee it, who will manage it? How are we going to tackle this, and work together in a proper fashion.
    * a.Top down give back license?
      * i.Anyone using the API has to provide access of their plugin/modification to ALL end users IF they release it publicly. Private plugins/modifications are subject to a different license or clause. This will prevent devs from picking and choosing who can use their software that they publicly released. Don’t hurt the end user.
  * 1.I’m not sure, if this will work, due to the fact that servers want, and have to be unique, e.g. i don’t like end-users being able to clone my games, and run them themselves after being awake for three days straight, writing a new gamemode.
  * 3.What license are we going to use?
    * a.3-clause BSD, LGPL, Apache 2.0, MIT, etc.
  * 4.Should we use a contributor license agreement (CLA)?
    * a.This would re-assign the copyright ownership of contributions to the project.
    * b.We would need a means of recording this data.
      * i.VCS like git / mercurial / svn / etc to track commits by project members.
      * ii.Having PR’s accepted would require agreeing to a CLA?
#要求
 * Can be used with an unmodified vanilla Minecraft client.
 * Has an abstraction layer. For example, rather than having to refer to, say, Minecraft’s Player object (or class specifically), plugins/mods refer to a separate independent Player object in Java. This means that if the Player object is removed from Minecraft, plugins/mods would not break because it was referring to this “virtual” Player object.
 * Established methods of accepting contributions (i.e. pull requests).
 * Absolutely cannot utilize GPL (and possibly LGPL) so we can avoid having to face this same situation again.
   * Possibility of MIT?
   * <asie> I'd say LGPL with a CLA that forbids anyone from closing the source code of your contribution.
     * You can’t ‘close’ the source of a GPL contribution.
##需要考虑的要求
 * UNIT TESTING!!!
   * As an ex-enterprise ‘developer’ we can’t start a new project at a scale like this, without proper testing, we should use a good testing suite, which allows us to ensure both bleeding, and stable builds are stable as-is.
 * Client and Server modification so users don’t require using multiple systems.
 * Quality Documentation, allowing the community to pick it up, easily.
   * We really really need to provide up to date documentation, allowing new users to quickly learn how ‘it’ works.
   * Possibly migration guides, and tips on migrating from old systems to this system.
 * Central Repository for plugins/mods.
   * Why should we have one? (FEEDBACK)
   * Trusted source for users.
   * Peer review code.
   * Requires scalable infrastructure, possibly cost intensive, reason why bukkit went to curse then mojang
     * We can also use Amazon for scalability
#引用
 * 全部来自 #nextstep 的IRC频道，除非另加注明
   * 1.<LexManos> Chunkr，没错，我要完全重写FML的登陆过程。最终的目标是允许原版客户端连接Forge服务端。在1.7.10中的问题是threadedness of the client和我并不想破坏协议兼容性的原因。
   * 2.<LexManos> 我有很严格的规矩遵守，将mod的兼容性控制在单一一个MC版本中，而新的MC版本就意味着我可以把那些新的狗屁东西搞得更好了。
   * 3.<LexManos> Dark_Arc, To be able to provide a platform that extends the most functionality to the end modder allowing for proper content and expansion, a ever evolving and adaptible interface to vanilla code is required. People would be crazy to say that it is possible to do 1/2 the shit modders do with a massive abstraction layer while maintaining my sanity on the development end. So yes ideally there would be two projects as there have existed sofar. Forge which is low level giving everyone access to what they want, and a abstraction layer {Bukkit} that provides a stable platform for the smaller general purpose things. This is why Bukkit and Forge have existed in harmony for so long. If the time comes where we need to official find a replacement for Bukkit's abstraction layer. I am all for it and will hope that whomever develops that {or helps me develop it} will be willing to work with me on a closer level then the Bukkit team has. This is why before this fiasco I was working with Blood to get Cauldron into a more maintainable and easier to develop state.
#API比较
 * Bukkit
   * 任何使用Bukkit的API的软件都将会变成Mojang奇思妙想的受害者，Mojang拥有Bukkit和它的API的版权。就像甲骨文对上谷歌一样。
 * BukkitForge
   * 使用Bukkit API，查看Bukkit的反对意见
 * Glowstone - https://github.com/SpaceManiac/Glowstone
   * 使用Bukkit API，查看Bukkit的反对意见
 * Canary - http://www.canarymod.net/books/api-reference
   * https://ci.visualillusionsent.net/job/CanaryLib/javadoc/ 
 * SpoutAPI - https://github.com/SpoutDev/Spout/tree/master/api/src/main/java/org/spout/api
   * (javadocs/感谢 Kashike) - http://vq.lc/ （全部） http://vq.lc/api/ （API）
   * https://github.com/SpoutDev/Spout/blob/master/LICENSE.txt 
   * 提交代码6个月之前使用LGPL，6个月之后使用MIT协议。目前所有代码使用MIT
     * 除了BukkitBridge兼容层使用的是
 * TridentSDK - https://github.com/TridentSDK
   * 没人认真的考虑过Trident
 * 开启一个新的FORGE API
   * http://xkcd.com/927/ 
 * 使用Mojang的官方API -
   * 可能一年之后才会出来，早就已经等了两年了。不予考虑。
