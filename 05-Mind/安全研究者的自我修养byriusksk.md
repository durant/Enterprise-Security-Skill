在上篇文章[《推荐今年C3黑客大会上的几个议题》](https://mp.weixin.qq.com/s?__biz=MzU0MzgzNTU0Mw==&mid=2247483908&idx=1&sn=9c99e59f416236ae3ace958252163991&chksm=fb0416fccc739feaaa457bd2c6723c36581b52d0c13914c9658cce4cbc56e42b360a3f703350&scene=21#wechat_redirect)中提到”Attacking Chrome IPC“这个议题，我觉得该议题最大的亮点是在前半场，作者nedwill是之前在Hack2Win大赛上因攻破Chrome浏览器而一战成名，他讲了如何训练漏洞研究能力的过程，讲述自己这几年在漏洞研究上的历程和心得，很励志，其建议也非常具有可操作性，值得效仿学习。我反复看了多遍，对其作了一些总结和补充。



# 1、刻意练习10000小时
这份“鸡汤”道理，想必大家都懂，就不解释了，不懂的自行百度，或者去读读《异类》这本经典书籍。

作者建议以月为单位来制定研究目标，他曾连续花了6个月的时间来研究Chrome Sandbox，但最终一无所获。

所以，有时坚持了不一定能达到目标，但不坚持，就更没戏了。



# 2、训练挖洞的双技能
（1）看洞：哪里看？历史漏洞的git log、bug报告、代码质量报告等等

（2）识洞：就是肉眼看代码找漏洞，即代码审计，难点也就是在这上面，训练方法继续往下看



# 3、代码审计训练
（1）根据自己目标定位，寻找相应的历史漏洞案例进行学习，比如要搞chrome就找chrome的历史漏洞

（2）掌握漏洞所在的模块或子系统，但不看完整的漏洞细节描述，尝试在漏洞版本中找出对应的漏洞

（3）如果（2）中未能找出漏洞，就去看漏洞细节描述，对比自己的审计过程，看遗漏了哪一步骤

（4）不断重复上述训练，直至相信：挖洞只是体力消耗，而非能力问题

这第4点说得，非常励志，因为挖洞挖久了，有时真的容易怀疑自己的能力，目标难度越大，越容易打击人。

作者第一次训练的漏洞是j00ru（Project Zero成员）的IDA漏洞：https://j00ru.vexillium.org/2014/10/secure-2014-slide-deck-and-hex-rays-ida-pro-advisories-published/，2014年的文章了



# 4、3~5年的训练计划
1~2年：做做 CTF 或 WarGames 题目，网上有很多CTF writeup可以参考学习

2~3年：简单点的目标，就是找相对容易挖的产品

3~5年：困难点的目标

目标的难易程度可以直接参考相应的产品的漏洞奖励计划或私有市场的价格，挑选出一份目标清单，按难易程度排序，逐一去实现它。



# 5、Fuzzing训练
作者代码审计2年后，才开始尝试Fuzzer开发。

（1）拿已公开的历史漏洞问自己：如何写fuzzer挖掘到此漏洞？

（2）如果自己不知道此漏洞，那又能够挖掘到呢？

（3）不断重复训练并改进fuzzer，相信会有更多漏洞被意外发现



# 6、努力往往比运气和天赋更重要
虽然挖洞也需要一定运气和天赋，但多数你认为的挖洞天才，其实只不过是花了比你多100倍，甚至更多的时间在这项技术研究上而已



# 7、进入研究者团队或社区，互相学习
国外的交流氛围会比国内的更好一些，也更愿意分享。

很多时候自己的交流圈，大多是一些熟识的同行，或者同事，一般可交流的人还是比较少的。

经常在网上看到不少人会问，如何认识xx大牛、黑客，但其实很多时候却是：

努力提高自己的专业能力，圈子最终会吸纳你进去认识更多圈内人。



# 8、建立自己的漏洞信息来源
RSS订阅无疑是自己最好的方式，这个需要依赖平时自己去不断收集订阅。

很多漏洞相关的博文，往往曝露出某些软件新的攻击面，抢占先机就显得尤为重要，比如当年Android stagefirght mp4漏洞、word公式编辑器、adobe图片转换器等等，如果能及时关注并尝试去挖掘，往往可以收获不少漏洞的。



# 9、收集和学习开源的漏洞挖掘工具
比如afl、honggfuzz、libfuzzer等很多优秀的漏洞挖掘工具，都是值得好好阅读代码，学习其中的fuzzing思路，可以更好地应用到未来的漏洞挖掘研究上。



# 10、很多不愿搞研究工作的挖洞人，只不过是为了权衡利弊
在《从0到1：开启商业与未来的秘密》一书中有一章叫做“秘密”，漏洞研究可以当作挖掘秘密，为什么人们不探索秘密呢？书中提到4种原因，我觉得同样适用于漏洞研究领域：

（1）渐进主义：把目标定得低一些，更容易取得好成绩；

（2）风险规避：人们害怕秘密是因为怕犯错，除此之外，可能也担心KPI没法完成，又或者挖洞拿到的奖金又该如何跟公司“分赃”呢？

（3）自满：很多时候，某些人可以坐享其成，又何必自己去挖掘秘密；国内研究氛围又喜欢搞营销吹牛逼，牛逼吹多了吹大了，有时连自己都信了；

（4）扁平化：任何一个拥有雄心壮志的人，在涉及某一研究领域之前都会问自己一个问题：如果有可能挖掘到漏洞，难道全球人才库中更加聪明、更加有技术能力的人还没有发现吗？这种怀疑的声音阻止了不少人去探索秘密，从事研究工作，因为身处的世界似乎大到任何个人都无法做出独特的贡献。

# 11、工具与方法论沉淀
虽说代码审计是项必备技能，但终究是项体力活。

有些漏洞（比如逻辑漏洞）可能就需要人工审计，但也有不少漏洞是可以自动化Fuzzing，一些能自动化或半自动化实现的，尽量写程序自动化。

因为，纯人工审计终究熬不过年纪，熬不过团队人员的离散变迁，熬不过互联网的快速发展……

比如，2012年刚开始写《漏洞战争》时，单身一人，从早上8点多起床吃饭，然后开始调代码、看代码，一直奋战到晚上12点，身体无压力。近7年过去了，现在要是这么折腾，身体就要散架了……

比如，团队里的人分工做不同领域的代码审计，若无工具和方法论沉淀，那么有人走的话，此人对应的领域可能就无法持续产出；若有新人加入，代码审计的技能又不好传承，很多又得重头来。所以，一直觉得，好的团队应该是，即使人员离散变迁，依然能够独立运作、持续产出。

比如，Linux内核在2018年净增87万行代码，很多类似复杂庞大的项目，看代码有时看都看不过来，一般都是针对性地挑模块作代码审计。

再比如，Fuzzer开发里面就有很多共用功能是可以直接做成框架沉淀下来，文件变异、崩溃监控、样本去重精简等等，很多时候有个新的攻击面需要测试，就可以直接在框架的基础上写fuzzer，将会高效很多。下文提到的一个IE漏洞挖掘案例就是基于这思路挖到的。

我曾经想开发两个漏洞挖掘系统，一个二进制，一个Web，名字都想好了，合称”冰弓玄箭“，就是英雄联盟中寒冰射手的那套装备，但一直都没什么业余时间去开发，仅写了个界面，希望2019年有机会能够完成：

![](https://github.com/AnyeDuke/Enterprise-Security-Skill/blob/master/05-Mind/beepress-image-95361-1547689933.jpeg)


”冰弓“的Logo直接用的是“破甲弓”，感觉是不是很酷……

再说说方法论，这词虽有点虚，但其实本质上就是一种技术方法的总结而已。

比如，渗透测试的时候，总有些人每次都能搞到RCE，无论啥网站，完全摆脱“随机挖洞”的命运。多数情况下，他们都会有一套自己测试方法，或者将一些经验转换成工具，测试时就拿自己的工具和以往总结的方法论开搞。

比如，STRIDE威胁建模本身就是一套方法论，一套简单的风险助记符，当然我这里不是说安全研究要用它，只是举个方法论的例子而已，它也没有那么万能。

写这么多，总结起来就一句话：多总结，多沉淀！



# 12、漏洞研究风向标：安全公告
如果大家有关注四大厂商（Google、Microsoft、Apple、Adobe）的安全公告的话，会发现有段时间会出现很多类似漏洞的公告，因为每次出现一个新的攻击面之后，一帮研究人员就蜂捅而上狂刷一波。

这种情况一向是先下手为强，而上文提到的工具和方法论就更显得尤为重要了，否则最后都只能捡剩的。

比如本周 Microsoft 安全公告出来后，我仔细分析了下，然后下班回家写了个Fuzzer，挂着跑了一天，出来个Crash，再用几分钟成功构造出PoC，实现IE浏览器的远程代码执行，可见也是个品相极佳的神洞：

![](https://github.com/AnyeDuke/Enterprise-Security-Skill/blob/master/05-Mind/beepress-image-95361-1547689934.jpeg)

但不幸的是，我打了1月的补丁后，发现修复了，成功“撞洞”，真的是欲哭无泪……

但至少证明，通过安全公告寻找新的攻击面，然后挖掘一些类似漏洞，一直是一种高效的漏洞研究方式。



# 13、老一辈研究者都去哪儿了？

![](https://github.com/AnyeDuke/Enterprise-Security-Skill/blob/master/05-Mind/beepress-image-95361-15476899341.jpeg)

最近腾讯AILab张潼离职的事传得很火，还有之前各大厂聘请的AI科学家陆续辞职，回归学术界，很多人因此唱起科学家之于科技公司的无用论，主要有以下几点原因：

研究成果无法落地为产品：做安全研究也是如此，很多事情是无法落地的，圈内很多研究团队都是拿漏洞来打比赛赚影响力，真正能实现为公司营利的（打比赛赚奖金的忽略不计，因为那些都不够给研究者们的工资），我只知道有1个研究团队/实验室今年营利了。

长期无产出，KPI压力大：研究了很长时间，最后仍一无所获，那KPI咋办、PPT怎么写、晋级怎么答辩。安全行业有句老话来形容安全研究工作，叫“三年不开锅，开锅吃三年”，但多数个人和企业都等不到三年。之前同事说王小云为何能破解出MD5，是因为她在学校里很长时间没搞出东西的时候，领导没找她麻烦，没有KPI压力，以致能够长期专注于此。具体原因我不确定，但学术界自然是没有企业有这般KPI压力。

业务数据不共享：业务部门的产品数据基本不太可能共享给实验室作研究的，一般都是实验室以SDK的形式提供给业务用，数据由业务自主控制。这种情况对于安全研究的影响相对较少一些。

头两点是多数安全研究者的困境，也跟圈内同行讨论过，下面聊聊这帮老一代“知青”最后都去哪儿了？这里我主要总结一些圈内人的应对方法（其实多数都是转型），具体不作点评，总结为主，也欢迎私信讨论（新注册的公众号已不允许留言）。

- 坚持研究：这帮人主要还是那些研究能力较强的，且有一定研究成果的人，围观下各大实验室就知道个大概了，不多说；

- 转型安全产品开发与运营：有产品就能解决落地问题，帮助企业解决实际问题，有不少人走这条道，去做威胁情报系统、漏洞扫描器、WAF、云安全产品等等；

- 转型业务安全：跟研究工作差异较大，因为业务安全的主要问题很多时候并非漏洞，而是跟业务产品相关的黑灰产对抗等等；

- 自由研究者：国外很多此类研究者，靠拿漏洞赏金过活，俗称“赏金猎人”，国内相对少一些，也有一些国内自由研究者后来又进企业做研究的，这里讲的几种转型都可以来回转换，有些人就干过。

- 创业：这里包括安全行业内的创业，也包括那些开淘宝店、奶茶店、服装生意、卖水果的……



# 14、个人终究干不过团队
有时想搞的研究太多了，但发现一个人根本搞不过来，需要多人协作才可能完成。但需要多人在研究领域上有交集，否则拉在一块也是各搞各的。

前篇第7点讲到“进入研究者团队或社区，互相学习”，也是一大影响因素，互相学习也是一种提高效率和产出的方式。

算了，不多说了！



后话
这次真的结束了，没有续篇了。

思考了很多，总结了很多，有些也是写了删，删了写。

安全研究领域一直也没人写过这些，出来唠叨几句，也欢迎大家私信讨论。

最后奉一首酒桌上的《苦行僧》结束本话题，听过这首歌很多个版本，包括原唱，但终究还是觉得视频里这位老哥唱得更具江湖气、更具情感、更具感染力……旁边一老哥听着听着都偷偷抹泪了！

之所以点这首歌，是因为：每一个研究者都是独立自行的苦行僧！

# 结语
今年因个人原因，已从安全研究转向业务安全，深知研究的不易。

相信安全领域有秘密的存在，虽会导致黑产的诞生，但肯定也会因此诞生一些优秀的研究者。

最后以白桦的《船》致敬所有仍在安全研究道路上前进的人，与诸君共勉：



我有过多次这样的奇遇，

从天堂到地狱只在瞬息之间：

每一朵可爱、温柔的浪花

都成了突然崛起、随即倾倒的高山。



每一滴海水都变脸色，

刚刚还是那样的美丽、蔚蓝；

旋涡纠缠着旋涡，

我被抛向高空又投进深渊……



当时我甚至想到过轻生，

眼前一片苦海无边；

放弃了希望就像放弃了舵柄，

在暴力之下只能沉默和哀叹。



今天我才有资格嘲笑昨天的自己，

为昨天落叶似的惶恐感到羞惭；

虚度了多少年华，

船身多次被礁石撞穿……



千万次在大洋里撒网，

才捕获到一点点生活的经验，

才恍然大悟，

啊！道理原是如此浅显；



你要航行吗?

必然会有千妖百怪出来阻拦；

暴虐的欺凌是它们的游戏，

制造灭亡是它们唯一的才干。



命中注定我要常常和它们相逢，

因为我的名字叫做船；

面对强大于自身千万倍的对手，

能援救自己的只有清醒和勇敢。



恐惧只能使自己盲目，

盲目只能夸大魔鬼的狰狞嘴脸；

也许我的样子比它们更可怕，

当我以命相拼，一往无前！



只要我还有一根完整的龙骨，

绝不驶进避风的港湾；

把生命放在征途上，

让勇敢来决定道路的宽窄、长短。



我完完全全的自由了，

船头成为埋葬它们的铁铲；

我在波浪中有节奏地跳跃，

就像荡着一个巨大的秋千。



即使它们终于把我撕碎，

变成一些残破的木片，

我不会沉沦，决不！

我还会在浪尖上飞旋。



后来者还会在残片上认出我，

未来的诗人会唱然长叹：

“这里有一个幸福的灵魂，

它曾经是一艘前进着的航船……”


