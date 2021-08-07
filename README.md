# burpsuite 安装 / Install	（linux&windows）

## 注：

本文所涉及到的工具均不是由本人开发或修改，不保证绝对安全，由使用本文提供工具所带来的一切后果自负

由于有新功能，汉化包是以前的，所以只有大部分能汉化，推荐英文版(请参考最下方图片)。`linux` 的中文版我并没有试过

本文及本人的对应仓库会不定时更新

`linux` 部分文字描述多， `windows` 部分图片多，可互相参考 `keygen` 不会轻易过期

一个很好的GitHub仓库，建议和本文同时查看	=>	https://github.com/Mr-xn/BurpSuite-collections

## linux

### 准备：

0、注：自行解决 `JDK / JRE` 的安装及配置环境变量，配置好后终端运行 `java --version` 

![image-20210806133010964](https://raw.githubusercontent.com/lavaicer/Img/main/image-20210806133010964.png)

1、官网下载 `.jar` 放到 `.zip` 解压后的文件夹目录下	--> https://portswigger.net/burp/releases/

2、下载 `linux_Burpsuite_pro.zip` 	=>	https://github.com/lavaicer/BurpSuite_Pro_Install/raw/main/linux_Burpsuite_pro.zip

### 安装：

1、把下载好的文件放在一个文件夹里，重命名官网的 `.jar` 为 `burpsuite_pro.jar` ，直接把文件夹放到你希望这个软件存在的位置。

例如： `/home/username/software/burpsuite`

重命名的好处：后面的命令会涉及到文件名，重命名的话后面官方更新的时候直接把高版本的改成 `burpsuite_pro.jar` 就可以了，比较省事。新版需要再次激活，所以 `keygen.jar` 不要删，到时执行 `java -jar keygen.jar` 再来激活一次就可以了。

2、文件夹目录下终端执行

英文

 `java --illegal-access=permit -Dfile.encoding=utf-8 -javaagent:./loader.jar -noverify -jar ./burpsuite_pro.jar`

中文

 `java --illegal-access=permit -Dfile.encoding=utf-8 -javaagent:./loaderCn.jar -noverify -jar ./burpsuite_pro.jar`

3、运行注册机 

`java -jar keygen.jar`

4、激活	（下面Windows部分有图片）

-   修改证书字符串为 `license to username` 的样子(也可以不管，无所谓)
-   从 `keygen.jar` 复制 `License key`，粘贴进 `Burp Suite Pro` 点击  `Next`
-   选择 `Manual Activation`
-   从 `burp` 复制 `License Request` 到 `keygen.jar` 的第二栏
-   从  `keygen.jar`复制 `license response` 到 `burp`，然后一路完成

5、添加执行命令到系统

-   `sudo vim /bin/burpsuite`

-   在新建文件中添加

    英文

    `java --illegal-access=permit -Dfile.encoding=utf-8 -javaagent:/home/username/software/burpsuite/loader.jar -noverify -jar /home/username/software/burpsuite/burpsuite_pro.jar`

    中文

    `java --illegal-access=permit -Dfile.encoding=utf-8 -javaagent:/home/username/software/burpsuite/loaderCn.jar -noverify -jar /home/username/software/burpsuite/burpsuite_pro.jar`

-   保存退出，为新建的文件添加执行权限

    `sudo chmod +x /bin/burpsuite`	

6、创建图标

上面应该已经可以从命令行启动了，不过这样总是感觉不舒服

进入应用目录`cd /usr/share/applications`

-   桌面没有 `burp`

    -   `cat *.desktop > burpsuite.desktop` ,将`Exec=sh -c` 一行改为 `Exec=sh -c "/usr/bin/burpsuite"`(`/usr/bin` 和 `/bin` 是一样的)，找个好看的图标把路径放上就大功告成了，不放图标就是透明的，也挺有意思

        ![image-20210806141504299](https://raw.githubusercontent.com/lavaicer/Img/main/image-20210806141504299.png)

-   桌面有 `burp`

    -   打开 `burp.desktop` 文件，将`Exec=sh -c` 一行改为 `Exec=sh -c "/usr/bin/burpsuite"`



### 注：

可能以后 `java` 版本会不适配 `burp`，到时候在安装指定的版本吧，或者参考下面 `win` 的方法，不依赖系统的 `JDK` 版本环境

参考文章：

https://github.com/SNGWN/Burp-Loader

https://www.iculture.cc/cybersecurity/pig=205

---

## win

### 注：

不依赖、不影响系统环境，自带 `JRE` ，激活之后添加快捷方式，再改个图标就大功告成

`*CN.vbs` 在Windows自带的实时保护下报毒打不开，可以关闭，下个其它的吧，我以前用火绒

**关闭Windows 安全中心中的Defender 防病毒保护**

1.  依次选择“开始” >“设置” >“更新和安全” >“Windows 安全中心”>“病毒和威胁防护”>“管理设置”（或在以前版本的**Windows 10** 中选择“病毒和威胁防护设置”）。
2.  将“实时保护”切换为“关”。 注意，计划的扫描将继续运行。



### 1、准备

1、官网下载 `.jar` 放到 `.zip` 解压后的文件夹目录下	--> https://portswigger.net/burp/releases/

2、下载 `win_Burpsuite_pro.zip` 	=>	https://github.com/lavaicer/BurpSuite_Pro_Install/raw/main/win_Burpsuite_pro.zip

解压到平时装软件的位置	

![image-20210807114501270](https://raw.githubusercontent.com/lavaicer/Img/main/image-20210807114501270.png)

### 2、安装

运行一种语言和注册机的脚本文件，和 `linux` 一样复制粘贴激活，版本更新的时候也是更改新版本的文件名为 `BurpSuite_Professional` +激活就可以。建议看一下脚本怎么写的以升级的时候自行修改

a	粘贴到 `burpsuite` 中，点击 `next`

![image-20210807114848780](https://raw.githubusercontent.com/lavaicer/Img/main/image-20210807114848780.png)

b	点击 `Manual activation`



c	点击 `copy request` 粘贴到注册机的第二栏，然后将注册机第三栏自动生成的复制到 `burpsuite` 的第三栏，点击 `Next` =>  `Finish`

![image-20210807115148213](https://raw.githubusercontent.com/lavaicer/Img/main/image-20210807115148213.png)

d	效果	

![image-20210807115415536](https://raw.githubusercontent.com/lavaicer/Img/main/image-20210807115415536.png)

![image-20210807120218389](https://raw.githubusercontent.com/lavaicer/Img/main/image-20210807120218389.png)

e	右键添加语言脚本的快捷方式，移动到桌面

![image-20210807122459721](https://raw.githubusercontent.com/lavaicer/Img/main/image-20210807122459721.png)

​	右键	=>	快捷方式	=>	更改图标	=>	图标路径找到图标	=>	确认

![image-20210807122855773](https://raw.githubusercontent.com/lavaicer/Img/main/image-20210807122855773.png)



参考文章：

挺久之前看到的，当时还没有记博客地址的习惯，这个压缩包被我存到硬盘里了。有人知道原博客可以发我一下地址。



## 汉化效果图：

大个的界面都没问题（图1），部分选项卡有英文（图2、图3）

![image-20210807124250812](https://raw.githubusercontent.com/lavaicer/Img/main/image-20210807124250812.png)

![image-20210807124343770](https://raw.githubusercontent.com/lavaicer/Img/main/image-20210807124343770.png)

![image-20210807124409758](https://raw.githubusercontent.com/lavaicer/Img/main/image-20210807124409758.png)


