# 阿屁屁制作心得：Github篇

## github是什么？

这是个好问题。我曾以为GitHub是高挂云端遥不可及的神器，勇敢地sign up后发现它也蛮平易近人和可爱的，就是取名方面创意独特了一点。GitHub有很不错的官方tutorial (https://guides.github.com/activities/hello-world/)，因此我也不step by step地赘述。这次想着重叙述GitHub是什么，并让你搞清楚GitHub是干什么用的。

## Repository - 把Projects保存在云端
首先，你有一个github account，而且手头上有几个project，称为“repository”。每个repository是一个文件夹，你把你的code和assets都上传到里面去。例如你的project是一个网站，里面就是一堆html文件（当然还有css和你的图片等）；你要做一个Android app，里面就是你的java和xml等等。当然我也看过开源字体里面有ttf、otf、ai等等。

这些文件显示在Code tab。你看，我的“firstapp” repository里面只有三个文件，其中README.md和_config.yml还不是我创建的。
![](https://i.imgur.com/p0SmISz.png)
也就是说，上述其中两个文件的location就是：
https://raw.githubusercontent.com/FooJiaYin/firstapp/master/README.md
https://raw.githubusercontent.com/FooJiaYin/firstapp/master/DSC02660.JPG

源文件放这里有几个好处：
1. 免费空间
2. 需要用的时候可以直接下载。
  文档：right click "raw" button→Save link as…（Left click会直接在browser打开喔）
  其他的点击download就可以了～
2. 可以download/clone整个repository。有几种方式：
  I. 点击download/clone下载zip
  II. 许多IDE从github import project的功能～目前用过比较普及的Visual Studio和Android Studio，还有cloud的CodeAnywhere都有喔！这样看来Eclipse应该也有。只是我还不会把更改推送回去，怎么大家的界面都不一样，到底要在哪里git……
  III. 下载git（不确定）
3. 可以查看version history
4. 可以和广大网民分享！

## Branch - Repository的分身

如果你仅仅认为GitHub是个云端空间，那就大错特错了！ 

![](https://guides.github.com/activities/hello-world/branching.png)
这张图片棒棒地诠释了branch的奥义。你手上有一个open source project。你当然不会让外面那些人对你写的代码胡作非为（想象我们collaborate的笔记被砍掉重练、胡乱涂鸦的头痛）。聪明的你于是为你的repository制造了无数分身（branch），让collaborator宝宝在上面动工。

他可以做你允许的任何操作，例如上传文件、重命名、改代码等等。改动过后，以电脑的逻辑我们照例要Save changes，上下左右找不到Save的字眼的宝宝别急，他改头换了面叫做Commit。这些更改需经过你审核，于是宝宝pull request通知你他改得高兴了。经过思考你觉得宝宝做得不错，于是你就把分身的新功能merge进正身里。

注：
- 你可以建立很多branch，正身只有一个，就是你的master branch，不可以删。其他的都是克隆的试验品。除了从master clone，也可以从其他branch clone出新的branch。在对新的branch做出更改/merge之前，他会保持和clone时的旧branch一模一样。
- 一个Pull request可以包括几个Commit一起发送，但只能有两个比对branch（不一定要从分身→Master，也可以分身/Master→分身避免被spam。
- Pull request像一个通知或post，宝宝可以写description告诉你详情。他还可以放file和@你，甚至用emoji卖萌呢。你也可以在下面comment。
- 你收到Pull Request时，Github会贴心地帮你比对改动的地方。
- Merge了commit后，只有被merge的branch会更改。你随时可以抛弃branch，或继续使用。
- Branch也可以用来做versions backup。某些时候你可能想回到过去。

## Issues和Project - Workflow管理。

**Issues**说白了就是一个论坛/group，让你和小伙伴好好地聊聊、分配任务、乔事情、达成共识。Issues = post，大家可以在下面comment。

这里的**Project**是指repository里面的中间那个tab，里面可以一览每个repository的subproject。一个project就是一个kanban，类似Trello那样有column然后可以放card。card的种类超少，只有request、issues（从sidebar拖进去）和note自己写。

注：
- Pull Requests和Issues可以用label和Milestone来分类，还有search bar和各种filter，查找十分方便。

GitHub有那么多COllaborate的功能，我看其实不是很需要3th-party吧。

## Open Source - 与别家的孩子一起成长。

>"参与别人的project是付出和进步最好的方式。"
>——世界最大的OpenSource Community，GitHub

毫无头绪的你可以到这里看看：https://github.com/explore 虽然尽是些高大上的玩意。

一般上，你可以对人家的public repository做这些事情：
1. **Watch**：接收这个repository的通知。
2. **Star**：收藏，留个纪念以后查找（之后可以去看看Your Stars）。
3. **Fork**：把整个repository复制到你的名下。修改后，可以给Owner send pull request，就像一个属于你的branch。
4. **Download/Clone**：保存到电脑或你的IDE，和你的GitHub account无关。
5. 在**Issues**下comment或建立new issue。

以及，**follow**其他users。

发现好的project，记得跟我分享喔 <3

## Github Pages - 免费host网站
详情：https://pages.github.com/

有两种模式，第一种只要你有html在手，在github上创建网站就是几秒钟的事。你只要开一个repository，把整个文件夹丢上去，然后在你的repository setting enable github pages。注意你的主页必须是master branch下面的index.html。

另一种是用github的template，这样你就不需要写html，只需要写好你的README.md就好。

以下是我建立的第一个能看的github，使用第一种模式。
Page：https://foojiayin.github.io/Sticky/
![](https://i.imgur.com/vcVsk5c.jpg)

html文件采用的是今年上半年学校的html作业。

这对我而言是个意外惊喜，圆满实现我的一桩心愿。我喜欢它免费，也喜欢它简洁明了的网址；喜欢它原始，喜欢它DIY，而不是说是不需编码却要下载一堆plugin折腾各种使用界面和术语。

我不需要statics，不需要database，我只要我的东西被看见，如此而已。




