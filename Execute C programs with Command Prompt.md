# Execute C/C++ programs with Command Prompt

- 不知道commander是什麼的同學請在windows search “cmd”，打開那個黑色的東東。
- 在這裡我們要使用 **[Linux指令](#Linux-指令)** 喔
- **執行C++的話以下的gcc指令全部要換成`g++`**

假設我在Desktop的"Testing" Folder裡有個testing.c，我想要compile它
1. 首先我們來到文件夾裡面（用`cd`）
2. Type `gcc testing.c` *to compile "testing.c" into an executable .exe file*

    ![](https://i.imgur.com/T5k0BD1.png)
    
    :::warning
    如果之前沒有做好[Environment Setting](#Setup-C-Environment)的話會出現這樣：
    
    ![](https://i.imgur.com/doXzgNc.png)
    
    然後如果你試著type `C:\MinGW\bin\gcc testing.c` 會出現一堆 “xxx.dll was not found" 之類的問題，所以還是乖乖去configure [Environment Setting](#Setup-C-Environment)吧
    :::
    
3. gcc by default會把新建立的.exe文件命名為"a.exe"。
    你會發現 "Testing" folder裡面多了一個叫做"a.exe"的file。

4. Type `a` *to run "a.exe"*

    ![](https://i.imgur.com/84n6UZV.png)
    不會開new window，會直接在Command Prompt裡執行。
   
5. 如果你覺得 "a.exe" 不夠特色，也可以建立其他名字的 .exe file：
    Type `gcc testing.c -o <filename>` *to build executable file as "<filename>.exe"*
    Type `<filename>` to execute it.
    
    ![](https://i.imgur.com/uPXMChs.png)

6. Type `gcc testing.c -o <filename> && <filename>` *to execute **immediately** after compilation*
    - `&&` 的作用是連接指令

## Setup C Environment

1. **Install C compiler** (We use **[MinGW](http://www.mingw.org/)** in this case)
    其實裝過CodeBlocks的應該都已經有MinGW在Program Files的CodeBlocks文件夾裡，但是可能版本不是最新的，package的directory很多也不一樣，為了免除一個個redirect的麻煩我還是選擇重新安裝。
    - Download **MinGW** [here](https://sourceforge.net/projects/mingw/files/)
    - Follow instructions [here](http://www.mingw.org/wiki/Getting_Started)
    :::info
    - 鼓勵set directory as `C:\MinGW`，如果裝在其他地方那麼其他相關的setup步驟也要注意保持一致！
    - 不需要安裝全部packages，但是基本的配備一定要有。
    新手裝：gdb、g++、gcc等等，沒有這些肯定跑不了。
    保險起見可以把安裝時的basic都勾選。
    - Add / remove package: Programmes -> MinGW Installation Manager
    不要怕裝錯packages，可以隨時用這個軟件更改
    :::
    
2. **Environment Setting**（很重要！！）
    上面的[instruction](http://www.mingw.org/wiki/Getting_Started)有寫，但是應該很多人都會忽略/懶得看，所以在這裡抄一次。

    > 1.  Right-click on your "My Computer" icon and select "Properties".
    > 2.  Click on the "Advanced" tab, then on the "Environment Variables" button.
    > 3.  You should be presented with a dialog box with two text boxes. The _**top**_ box shows your _**user**_ settings. The PATH entry in this box is the one you want to modify. Note that the bottom text box allows you to change the _**system**_ PATH variable. You _**should not**_ alter the system path variable in any manner, or you will cause all sorts of problems for you and your computer!

    或是直接開window search：（記得是下面for your account那個喔！）
    
    ![](https://i.imgur.com/61hKVCT.png)

    > 4.  Click on the PATH entry in the TOP box, then click on the "Edit" button

    ![](https://i.imgur.com/mbmOT2w.png)
    
    > 5.  Scroll to the end of the string and _**at the end add**_  
    >     
    >     ```
    >     ;<installation-directory>\bin
    >     ```
    也可以直接按`New` 然後type你的directory：
    
    ![](https://i.imgur.com/oKH55GG.png)

    > 6.  press OK -> OK -> OK and you are done.
    > 
    > **NOTE**: Substitute <installation-directory> with the FULL _absolute_ path name of the installation target directory you chose (ie C:\\MinGW);
    > 

3. **或是直接用cmd**

    先找到compiler的directory：
    ```
    where gcc 
    ```
    cmd會印出directory，copy下來，然後打這段：
    ```
    SETX PATH "%PATH%;<path>" //<path>替換成剛剛copy下來的address
    ```
    Example:
    ![](https://i.imgur.com/ZLQVN0q.png)



## Linux 指令
1. cd：切換路徑

    ```
        cd project_1     //進入 project_1 資料夾
        
        cd ..      // 回到上層資料夾
    ```
2. ls：列出此目錄內所有東西

3. rm：刪除

    ```
        rm code.c //刪除 code.c 這個檔案
        
        rm -r project_1 //刪除 project_1 這個資料夾
    ```
4. mkdir：建立資料夾

    ```
        mkdir project_1 //建立 project_1 這個資料夾
    ```
5. passwd：更改密碼

6. mv：移動檔案（到子目錄）

    ```
        mv 檔名 資料夾名稱/
        
        mv code.c project_1/    //移動 code.c 到 project_1 資料夾裡
        
        mv code.c ..       //移動 code.c 到 上層資料夾裡
    ```

7. cp：複製（copy)

    ```
        cp 檔名 目的地
        
        cp code.c project_1/a/b1     //移動 code.c 到 project_1/a/b1
    ```

8. vim：文字編輯器

    ```
        vim code.c    //編輯 code.c 這個檔案，如果這個檔案不存在，他會自行創建一個
    ```
    
9. 從 `C:\` 到 `D:\`
    不要打`cd`！直接打 `D:`就好了！

更多指令可自行上網搜尋，或至[鳥哥的 Linux 私房菜](http://linux.vbird.org/linux_basic/redhat6.1/linux_06command.php)參考