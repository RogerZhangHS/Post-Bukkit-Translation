我们正在对于我们的之后的未来进行一项公众调查，以让我们决定我们之后的何去何从，在目前这个情况下，你可以加入IRC频道 irc.esper.net 6667 #nextstep。
这个文档受许多从#nextstep频道中来的具有共识的人们而编辑。在加入讨论之前请先请仔细阅读整个文档，因为你所提出的意见可能早已被提出。
发生了什么？

    请务必帮助我们完成这份调查！（需要翻墙）：http://bit.ly/1qnO8Gm
    你可以点击这里查看调查的结果：https://docs.google.com/forms/d/1lQ0eXyfaEHJPutFPAtNQk2XQteqHSKT4OJXWGFNfVio/viewanalytics

##话题是什么？
    净室软件开发？	     
	    不。为什么？在我们所知的范围内并没有任何Minecraft的Java接口支持净室软件开发。所以，我们完全逃不掉EULA的限制。
        不。太多开发者们已经深入研究了Minecraft源代码太多了，完全算不上净室软件开发的范畴了。

    在目前的MOD平台上构建？
        FORGE。为什么？早已经建立的玩家社群，避免了从头开始的困境。

    用什么API？
        CANARY或SPOUT。详情请看调查问卷结果。
		
##目录：
    发生了什么？
    目录
    最受欢迎的意见
    所有可用的意见
    备注
    问题
    要求
    引用
    API比较
	
##Most Popular Option
The prevailing opinion so far is to write a new abstracted API (as in it does not refer to Minecraft objects 1:1), sort of like Bukkit, on top of Minecraft Forge and possibly also Glowstone.
Forge is a client and server API that is popular with many gameplay mods. It already has a large community.
Because Forge features no “abstraction API,” a mod/plugin written for Forge may break between MC versions if Mojang makes too many large changes. Therefore, if an API is written on top of Forge, this problem should be alleviated.
Forge mods using this abstraction API will be able to use the rest of Forge, which is akin to using NMS in Bukkit, except much more power will be afforded to the modder.
This statement is wrong. Using an abstraction layer is like using Bukkit’s actual API and not touching anything in NMS.  There’s no spec for said abstraction, so it can’t be compared to using NMS.  Forge by itself IS using NMS, any abstraction on top of it is going to be more limiting (and most likely extremely)
Glowstone is a standalone reimplementation of the MC server. It is not based off of Mojang’s code like Bukkit, Forge, Spigot, and Canary. 
It has been suggested that whichever API the community agrees upon could also be built on top of Glowstone. 
Currently Glowstone already implements the Bukkit API and this is possible because Glowstone does not make use of proprietary Minecraft code.
Simply switching to a standalone re-implementation of the MC server is not an option for a lot of people because it will likely not be up to date in regards to new MC features, which is a problem when a lot of people are running regular creative or survival servers.
This is speculative, for instance features were available in Spout while features were still in prerelease for the MC server when the project is active.  This is all dependent on developer activity and quickness of patch updates along with complexity of the features.
While a brand new API could be written, it has been suggested that either the API of Spout (NOT Spoutcraft) or Canary can be re-used for this effort, which saves everyone work. It does not mean that whatever the resulting project would be would ingest significant concrete code from either projects.



##所有可用的意见
所有可用的意见
注：某些建议是由其他服务端的开发者所撰写的，由此，可能会有一些偏见。
1、换至Bukkit的竞争对手
    a、换至Canary平台
            i.Canary包含官方的 minecraft_server ，因此会违反服务条款（重要）
            ii.玩家社群并不大
            iii.使用BSD 3-Clause License
            iv.人们会想将Canary和Forge一起使用，Canary Lib可以被用作未来的类似于Cauldron服务端的东西。（Canary团队正在关注）
            v.他们的网站上文档详细
            vi.可以使用抽象层，就像Bukkit具有的那样。包含许多Bukkit本身具有的功能，同时也有许多被需要的API功能
                a. NBT仅仅是一小部分
            vii.团队建立时间较长
                尽管如此，但团队人数较少，并不能十分迅速的开发
            viii.一些在Bukkit平台上十分受欢迎的插件也同样兼容Canary
    b、换至 Minecraft Forge （并内置一个API）
            i.较大的玩家社群，被许多MOD所使用（加分）
                与Bukkit有着不同的思想，Forge通过使用API尝试暴露尽可能多的NMS代码。但是Bukkit将所有东西都隐藏在抽象层后面。
            ii.需要一个经过修改的客户端才能使用，但根据LexManos，可能在1.8后就不再需要了
			iii.每过一个版本，特定种类的MOD就不能够使用（重要）
			    Forge现在和今后都不会提供抽象层，因此哪怕是一些很小的Minecraft更新，MOD作者也需要更新他的作品。
				srgname OBF帮助。但并没有像Bukkit里面那样的write-once-ignore之类的东西。
				当然这些仅限于大型的计划，一些小型的MOD仅仅使用Forge API的接口
			iv.在Bukkit和Spigot上面的性能表现欠佳
			    可以被'修复'，但需要时间和人手
				    a.我们能尝试使用Spigot的优化嘛？
					    i.可以，但需要书面许可
					b.我们能使用现在已有的优化程序嘛？
					    i.首先我们需要清楚这些优化程序能不能让服务端的性能表现像当前的服务端一样。要不然这完全没有意义
						ii.有可能性，但我们也需要提前询问。并且我们要搞清楚我们所做的事儿有多少侵略性。
			v.对于开发者的易用性差
			    有一些（或很多）开发者认为Forge难以使用
				
This only applies to LARGE projects, some really tiny mods only interface with Forge API
Performance is subpar to both Bukkit and Spigot
Can be ‘fixed’ but will need both time, and manpower, mostly time.
Can we attempt to salvage spigot patches?
Yes, we could but we should ask written permission (FEEDBACK)
Can we use existing performance enhancement projects? (FEEDBACK)
Reason i’m putting it here, we need to know if we can easily get the server up to the known performance current ‘generation’ servers have, otherwise there won’t be any added value.
Might be possible, just that we might have to ask first. There’s also the question of how invasive things should be
Not very developer friendly
Considered “hard to get into” by some (or many?) developers
Lacks proper PR processing systems, unlike bukkit.
If the community is big enough, we can possibly apply pressure on LexManos?
Lack of documentation, though can be fixed
Community-made tutorials available on forums, though nothing beats the official ones
Lacks full Bukkit equivalents though this can be fixed
Switch to an independent clean-room implementation:
Switch to Glowstone
Project has been around for a long time, actually pretty up to date.
Missing very large portions of functionality, such as W-Gen, 
Generally out of date with Minecraft’s newer features because it is an independent from-scratch re-implementation of Minecraft’s mechanics (MAJOR)
Can use Bukkit API (PLUS)
Includes Bukkit API.  Possible License restrictions/issues (MAJOR)
Cannot combine with Forge mods (MAJOR)
Switch to MCServer
Written in C++
Possibly very fast (PLUS)
Unless a Java binding is added, all current Java code would have to be re-written in Lua (MAJOR)
Multi Protocol! Minecraft 1.2 all the way up to Minecraft 1.7.10 (PLUS)
Cannot combine with Forge mods (MAJOR)
Switch to Craft.net
Written in C#
Cannot combine with Forge mods (MAJOR)
Switch to Spout
Currently not in active development. It is “continued” under the name flow-engine in the flow github repository. Either Spout or flow-engine would need to be forked.
Out of date with Minecraft’s newer features because it is an independent from-scratch re-implementation of Minecraft’s mechanics (MAJOR)
Out of the box, Spout is simply an engine (client/server) You need the Vanilla plugin to get Minecraft
BukkitBridge module for compatibility has (MAJOR) performance problems given explicit design choices.
Unless creating a client is desired, Spout would need to have its client portion removed. Might even consider merging Vanilla’s code into Spout to make it a true Minecraft server.
Cannot combine with Forge mods (MAJOR)
Implement the Bukkit API on top of an existing implementation (Forge, Canary)
BukkitForge
Built on top of Forge
Has been around for some time, but abandoned since MC 1.5.2 (MAJOR)
Code still contains bukkit API - Possible License restrictions/issues (MAJOR)
Start anew and implement a new API or the Bukkit API
Switch to TridentSDK
Somewhat recent, however if we wanted to start with a small base this would be the way to go
Bad idea - Chunkr. This project is too immature
Start our own project
Lots, and lots of work (MAJOR)
Should be partly, or mostly compatible using the current api’s
Ability to pick a good licence, possibly GNU? GPL? LGPL? MIT?!
This would allow us the most freedom with what we’d want to do moving forward
The possibility to remap existing bukkit plugins to new API, with 90+%? compatibility (FEEDBACK)
Would it be possible to integrate with Forge API?
Should be transparent and open towards the community
Runtime patch with current Bukkit and Craftbukkit code (i.e. Mojang’s code is never distributed in the same binary as the GPL code -- rather, it is combined when the user runs the server)
Very dangerous in regards to Bukkit’s licensing situation (MAJOR)
Can use Bukkit API (PLUS)
Bukkit API is Mojang owned, may not be a plus
Install patch with current Bukkit and Craftbukkit code  (i.e. Mojang’s code is never distributed in the same binary as the GPL code -- rather, it is combined via a simple installer, which allows users to build their own server, using our, and their own patches)
Less dangerous, but still very dangerous in regards to Bukkit’s licensing situation  (MAJOR).
We can ‘ditch’ most if not all bukkit code, and use our own implementation, the default server already has most parts we need, all we need to add is a good API, which isn’t a whole lot of work, but certainly less work than writing a entire server from scratch, opinions?
Not sure whether it’s just a good idea, maybe keep the bukkit API and reimplement craftbukkit?
Possibly ‘more’ legal than distributing the minecraft-server.jar
Can use Bukkit API (PLUS)
Wait until Mojang releases the API
May be a very long wait, potentially years (we waited 2, and are still waiting) (MAJOR)
It will be an step up from Bukkit in what you can do, but it will not compare to Forge, et. al. which permit client modding because you will not be able to execute your own code on the client 
Possibly the lamest api we’ve ever seen, looking at the current possibility’s using command blocks, e.g. totally written, and made to be used on realms. Likely won’t compare to the extensible changes possible with current APIs.
Considering what Mojang’s been doing recently, could it be a ploy to force people on realms (conspiracy theory)
Implement a plugin API that acts as a wrapper around the Minecraft server
May even work on snapshots
Likely very fast to update (MAJOR)
Very limited as to what can be done (MAJOR)
Can only do what can be done by modifying network packets or reusing what can be done with command blocks 
##Notes
With nearly everything at this point in the Minecraft community being written in Java, a Java based server would probably gain the most support.
Using the current minecraft-server.jar is the easiest way to go, distributing patches which patch the server-code to insert ‘our’ code, allows experienced users to use java reflection to change base code, and use things we haven’t implemented in the API yet.
Vanilla clients need to be able to connect to it. Quite simply, if we’re looking for a post-Bukkit option, it’ll have to be this way. (MAJOR)
##Questions
Are we going to stick to ONE protocol, or are we planning to be MULTI protocol.
Only applies if we’re going to write our own software.
Really doesn’t matter, as we can simply update the protocol as MC updates come out. Mojang will probably keep updating the protocol a tiny smudge in areas, making multi protocol nearly impossible anyways.
The current status quo is that Bukkit/MC isn’t multiprotocol, so not too many people will really care for this I imagine
Ownership, how will this be ‘run’ who will oversee it, who will manage it? How are we going to tackle this, and work together in a proper fashion.
Top down give back license?
Anyone using the API has to provide access of their plugin/modification to ALL end users IF they release it publicly. Private plugins/modifications are subject to a different license or clause. This will prevent devs from picking and choosing who can use their software that they publicly released. Don’t hurt the end user.
I’m not sure, if this will work, due to the fact that servers want, and have to be unique, e.g. i don’t like end-users being able to clone my games, and run them themselves after being awake for three days straight, writing a new gamemode.
What license are we going to use?
3-clause BSD, LGPL, Apache 2.0, MIT, etc.
Should we use a contributor license agreement (CLA)?
This would re-assign the copyright ownership of contributions to the project.
We would need a means of recording this data.
VCS like git / mercurial / svn / etc to track commits by project members.
Having PR’s accepted would require agreeing to a CLA?
##Requirements
Can be used with an unmodified vanilla Minecraft client.
Has an abstraction layer. For example, rather than having to refer to, say, Minecraft’s Player object (or class specifically), plugins/mods refer to a separate independent Player object in Java. This means that if the Player object is removed from Minecraft, plugins/mods would not break because it was referring to this “virtual” Player object.
Established methods of accepting contributions (i.e. pull requests).
Absolutely cannot utilize GPL (and possibly LGPL) so we can avoid having to face this same situation again.
Possibility of MIT?
<asie> I'd say LGPL with a CLA that forbids anyone from closing the source code of your contribution.
You can’t ‘close’ the source of a GPL contribution.
##Requirements to Consider
UNIT TESTING!!!
As an ex-enterprise ‘developer’ we can’t start a new project at a scale like this, without proper testing, we should use a good testing suite, which allows us to ensure both bleeding, and stable builds are stable as-is.
Client and Server modification so users don’t require using multiple systems.
Quality Documentation, allowing the community to pick it up, easily.
We really really need to provide up to date documentation, allowing new users to quickly learn how ‘it’ works.
Possibly migration guides, and tips on migrating from old systems to this system.
Central Repository for plugins/mods.
Why should we have one? (FEEDBACK)
Trusted source for users.
Peer review code.
Requires scalable infrastructure, possibly cost intensive, reason why bukkit went to curse then mojang
We can also use Amazon for scalability
##Citations
All from #nextstep irc unless otherwise stated
<LexManos> Chunkr, Yes, in 1.8 I am going to compleetly re-write the FML login process. The end goal being to allow vanilla clients to connect to Forge server. Issue with doing it in 1.7.10 is the threadedness of the client combined with the fact that I do not want to break protocol compatibility.
< LexManos> I have strict guidelines to follow, keep mod compatiblity within a single MC version, new MC versions means I can break all the shit for the better.
<LexManos> Dark_Arc, To be able to provide a platform that extends the most functionality to the end modder allowing for proper content and expansion, a ever evolving and adaptible interface to vanilla code is required. People would be crazy to say that it is possible to do 1/2 the shit modders do with a massive abstraction layer while maintaining my sanity on the development end. So yes ideally there would be two projects as there have existed sofar. Forge which is low level giving everyone access to what they want, and a abstraction layer {Bukkit} that provides a stable platform for the smaller general purpose things. This is why Bukkit and Forge have existed in harmony for so long. If the time comes where we need to official find a replacement for Bukkit's abstraction layer. I am all for it and will hope that whomever develops that {or helps me develop it} will be willing to work with me on a closer level then the Bukkit team has. This is why before this fiasco I was working with Blood to get Cauldron into a more maintainable and easier to develop state.
API Comparison
Bukkit
Anything that would utilize the Bukkit API would be subject to the whim of Mojang, as Mojang owns Bukkit and APIs are copyrightable, per Oracle vs Google. 
BukkitForge
Bukkit api, see bukkit negative
Glowstone - https://github.com/SpaceManiac/Glowstone
Bukkit api, see bukkit negative
Canary - http://www.canarymod.net/books/api-reference
https://ci.visualillusionsent.net/job/CanaryLib/javadoc/ 
SpoutAPI - https://github.com/SpoutDev/Spout/tree/master/api/src/main/java/org/spout/api
(javadocs/thanks Kashike) - http://vq.lc/ (all) http://vq.lc/api/ (API)
https://github.com/SpoutDev/Spout/blob/master/LICENSE.txt 
LGPL unless commits are 6 months old, then it is MIT. All of SpoutAPI’s current code is MIT
Except for the BukkitBridge compat layer which is GPL.
TridentSDK - https://github.com/TridentSDK
No one has seriously considered trident
Start a new Forge API
http://xkcd.com/927/ 
Wait for Mojang API -
Will be year or more away, already waited two since it was promised. Not a viable option.
