# Learning BAT file

一开始是为了给folder做一个文件列表。回想起来，碰上需要列出清单的情况一共有三次一共有三次：

1. 缘起：想要整理百度云ebook书目给阿文！
2. 交毕业刊文件给出版社时做的资料清单。
3. 从毕业刊感言folder里面list出各班的名单。
4. 给电脑搬家时记录下原本的生态环境，方便以后留念。怎么有点怪。

我呈交文件时喜欢列一个表写目录，方便自己人家检查看有没有遗漏。（文书交接那会儿还不知道这玩意实在是太可惜了）除了办事交接妥妥的，我们在平常也可以给文件编列索引，一目了然也方便查找（比search bar快一百倍），尤其阿尹这种巴不得给自己一生编上目录的记录控和整理狂而言（只限于资料）十分重要！所以找到这个方法时我有多激动，你感受下！

想起陈舜臣先生曾在《日本人与中国人》里提到，“中国人是目录专家，日本人是保存天才”，古人见到现今的技术大概会非常感概吧。

# Tutorial
好教程不必多。

1. [使用dir產生資料夾清單](http://montaigne7j.blogspot.my/2014/03/dir.html)
  这篇介绍得很好，详细说明所有需要用到的command的含义。list.txt篇的各种变体便是由此而来。

2. 这个网站(https://www.zybuluo.com/yangfch3/note/338252)属于授人以渔一类，参透以后就可以玩各种花样，是说，应付各种需求了。

PS：如果连接失效了就看看evernote的[笔记](https://www.evernote.com/shard/s254/sh/f6e4c066-d281-421c-96d2-64ae566ede01/6e671fe9a1b13d8cc632c325adac449c)。

# 如何操作BAT file？

### STEP 1：编写

1. 打开notepad/其他text editor输入code（下面会介绍）。
![](https://i.imgur.com/zd5tSGq.png)

2. Save as * .bat（*可以放任何你喜欢的名字）
  记得type要选**All Files！All Files！All Files！！！**
![](https://i.imgur.com/gbaJIBR.png)

### STEP 2：运行

1. 把文件拖进你想建立清单的folder里，然后双击。
2. 看到新的txt file吗？打开来验收成果吧！

真是有够简单啊。

# list.txt篇

### 基本款：
```
@echo off 
dir /b /on > list.txt
```
* 包括subfolder但不包括里面的资料
* `/b`表示不要废话是要档案列表
* `/on`表示跟名字排序。（subfolder和其他文件排在一起）
* `> list.txt`把清单列表写进一个叫做list的txt文件。当然你要换成files.txt什么的也可以啦。

结果：
>Cover Folder.zip
getlisttxt.bat
list.txt
New folder
protfolio
Shisui Folder.zip
shisui.indd

### `dir`

```
@echo off
dir C:\Users\YIn\Desktop /b /on > list.txt
```
* 你可以在dir后面放上任何一个folder的path，这和把没有path的bat文件移到该folder里面运行的效果完全没有差别。由于我们没必要这么折腾自己，所以就放着不管好了。

### 如果不放`/b`会怎么样呢？
```
@echo off
dir /on > list.txt
```
结果：
![](https://i.imgur.com/wn2WFH7.png)
……就是这个乱七八糟的丑样子。（抱歉我不想写出来）所以我们还是放`/b`吧。

### 变体1：把subfolder排在上面

```
@echo off
dir /b /og > list.txt
```
* `/o`是排列方式，`/og`是指先排subfolder
* 其他排列方式请参考进阶说明。

结果：
>protfolio
New folder
list.txt
getlisttxt.bat
Cover Folder.zip
Shisui Folder.zip
shisui.indd

### 变体2：显示subfolder里面的资料

```
@echo off
dir /b /s /og > sublist.txt
```
* `/s`显示subfolder里面的资料的同时，也会将完整的path显示出来
* subfolder也会一并显示，但是不会和里面的资料排列在一起。因为`og`把subfolder移到最上面，而会subfolder里的资料会在母folder的资料列完后才列在下面。

结果：
>C:\Users\YIn\Desktop\protfolio
C:\Users\YIn\Desktop\New folder
C:\Users\YIn\Desktop\list.txt
C:\Users\YIn\Desktop\getlisttxt.bat
C:\Users\YIn\Desktop\Cover Folder.zip
C:\Users\YIn\Desktop\Shisui Folder.zip
C:\Users\YIn\Desktop\shisui.indd
C:\Users\YIn\Desktop\New folder\computer project
C:\Users\YIn\Desktop\New folder\computer project\project
C:\Users\YIn\Desktop\New folder\computer project\inquery-form.html
C:\Users\YIn\Desktop\New folder\computer project\menu.html
C:\Users\YIn\Desktop\New folder\computer project\project\css
C:\Users\YIn\Desktop\New folder\computer project\project\img
C:\Users\YIn\Desktop\New folder\computer project\project\contact-hongkong.html
*……下略*

提示：如果不想看到前面长长的path可以用notepad/text editor的replace功能（Ctrl+H）
![](https://i.imgur.com/T3a2NUK.png)
然后点击Replace All。TADAA！！
>protfolio
New folder
list.txt
getlisttxt.bat
Cover Folder.zip
Shisui Folder.zip
shisui.indd
New folder\computer project
New folder\computer project\project
New folder\computer project\inquery-form.html
New folder\computer project\menu.html
New folder\computer project\project\css
New folder\computer project\project\img
New folder\computer project\project\contact-hongkong.html

### 变体3：不显示subfolder名，但显示里面的资料
```
@echo off
dir /a:-d /b /s > sublist.txt
```
* 用`/a`command这顶要显示的档案类型。`d`是指folder name，`/a:-d`表示不显示folder name。
* 其他类型请参考进阶说明。
* 不需要把folder name列在前面，所以去掉`/og`指令。

Replace前面的path就不细说了。来看结果：
>list.txt
getlisttxt.bat
Cover Folder.zip
Shisui Folder.zip
shisui.indd
New folder\computer project
New folder\computer project\project
New folder\computer project\inquery-form.html
New folder\computer project\menu.html
New folder\computer project\project\css
New folder\computer project\project\img
New folder\computer project\project\contact-hongkong.html

## 进阶介绍
来源：[使用dir產生資料夾清單](http://montaigne7j.blogspot.my/2014/03/dir.html)

>DIR [drive:][path][filename] [/A[[:]attributes]] [/B] [/C] [/D] [/L] [/N]
[/O[[:]sortorder]] [/P] [/Q] [/S] [/T[[:]timefield]] [/W] [/X] [/4]
>
>[drive:][path][filename]：指定要顯示的磁碟機、目錄或檔案。
/A ：依照指定的檔案屬性來顯示檔案。
attributes
    D：目錄（folder）
    R：唯讀檔
    H：隱藏檔
    A：保存檔
    S：系統檔案 - 無意義
/B：使用單純格式 (沒有標頭資訊或摘要)。
/C： 顯示檔案大小千位數分隔符號。這是
/D：與寬的列表格式相同，但是依照欄來排序。
/L ：使用小寫顯示。
/N： 使用新的長列表格式，檔名會顯示在最右方。
/O： 依照指定的排序順序來列出檔案。
sortorder
    N： 依名稱 (英文字母)
    S ：依大小 (最小的在前)
    E ：依副檔名 (英文字母) D 依照日期與時間 (日期較早的在前)
    G ：先列出子目錄 - 表示相反的順序
/P：當資料填滿整個螢幕時暫停顯示。
/Q：顯示檔案擁有者。
/S：顯示指定目錄及所有子目錄中的檔案。
/T：指定用來顯示或排序的時間欄位
timefield
    C：建立
    A：上次檔案存取時間
    W：上次寫入檔案時間
/W：使用寬的列表格式。
/X ：顯示對非 8.3 格式的檔案產生的短檔名。
這個格式和 /N 相同，但是短檔名會插入在長檔名之前。 如果沒有長檔名存在，該處會顯示空白。
/4：顯示四位數的年份


# 解决中文显示乱码问题
由于运行bat是用ANSI语言，而ANSI不支持汉语系字体（以上都是猜的），所以中文、日文、韩文一律无法显示，会表示成??????????。看得我脑袋里也塞满问号……

**这是一个非常严重的问题。** 让我们动起手脚来解决吧！

### 方法1：成功率10%
**(https://2cyr.com/decode/?lang=en)**
通过网站转换encoding消除乱码。使用以来只成功过一次。

不过，这个网站可以preview对比各种encoding转换结果再实施转换，实在是非常贴心的设定！虽然用在这里的成功率低了一点，但是平常想要消除乱码（比如download zip的时候）也是非常不错的神器哪，推荐推荐！

### 方法2：失败
**把bat file改成ANSI档**——在[论坛](http://www.bathome.net/viewthread.php?tid=24088)上听说这样就可以解决问题。

……骗人的。

不过，这或许是其中一个步骤，以后还是沿用ANSI保险点。

### 方法3：成功！！

**干脆直接显示在cmd.exe里面然后copy。**

于是，我们需要修改一下bat文件：
```
dir /a:-d /b /s /og /t:a 
pause
```

1. 把`@echo off`去掉
2. 去掉` > sublist.txt`，因为不需要自动生成txt文件。 :(
3. 在下面加上一行`pause`，避免窗口直接关闭来不及复制。
这是目前为止最有效的方法。唯一的缺点就是麻烦，不只不能自动生成txt文件，文档太多时要复制超长的list也很令人头痛。

## 待续
当然，batch file除了上述简单的功能，还能批次处理许多操作。Rename、Move等等的也能很轻易办到喔，虽然我还没尝试。还有其他用途等着去发掘呢，好期待呀！

