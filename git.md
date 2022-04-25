# Git

##  起步  —  关于版本控制





### 1. 文件的版本

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204242157857.png)





### 2. 版本控制软件

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204242159407.png)





### 3. 使用版本控制软件的好处

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204242200633.png)





### 4. 版本控制系统的分类

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204242200764.png)





### 5. 本地版本控制系统

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204250838582.png)

特点：
使用软件来记录文件的不同版本，提高了工作效率，降低了手动维护版本的出错率

缺点：
**单机运行，不支持多人协作开发**
版本数据库故障后，所有历史更新记录会丢失





### 6. 集中化的版本控制系统

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204250842833.png)

特点：基于服务器、客户端的运行模式
服务器保存文件的所有更新记录
**客户端只保留最新的文件版本**

优点：联网运行，支持多人协作开发

缺点：
不支持离线提交版本更新
中心服务器崩溃后，所有人无法正常工作
版本数据库故障后，所有历史更新记录会丢失

典型代表：SVN





### 7. 分布式版本控制系统

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204250845438.png)

特点：基于服务器、客户端的运行模式
服务器保存文件的所有更新版本
**客户端是服务器的完整备份**，并不是只保留文件的最新版本

优点：
联网运行，支持多人协作开发
客户端**断网**后**支持离线本地提交**版本更新
服务器故障或损坏后，可使用任何一个客户端的备份进行恢复

典型代表：Git







## Git 基础概念





### 1.  什么是 Git

Git 是一个**开源的分布式版本控制系统**，是目前世界上**最先进**、**最流**

**行**的版本控制系统。可以快速高效地处理从很小到非常大的项目

版本管理。

特点：项目越大越复杂，协同开发者越多，越能体现出 Git 的**高性能**和**高可用性**！





### 2. Git 的特性

Git 之所以快速和高效，主要依赖于它的如下两个特性：

+ 直接记录快照，而非差异比较
+ 近乎所有操作都是本地执行





#### ①  SVN 的差异比较

传统的版本控制系统（例如 SVN）是**基于差异**的版本控制 ，它们存储的是**一组基本文件**和**每个文件随时间逐步累积的差异 **。

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204250850657.png)

好处 ：节省磁盘空间
缺点 ：**耗时**、**效率低**
            在每次切换版本的时候，都需要在基本文件的基础上，应用每个差异，从而生成目标版本对应的文件。





#### ② Git 的记录快照

`Git` 快照是在原有文件版本的基础上重新生成一份新的文件 ，**类似于备份 **。为了效率 ，如果文件没有修改 ，Git 不再重新存储该文件，而是只保留一个链接指向之前存储的文件 。

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204250854770.png)

缺点：**占用磁盘空间较大**
优点：版本切换时非常快，因为每个版本都是完整的文件快照，切换版本时直接恢复目标版本的快照即可。
特点：**空间换时间**





#### ③ 近乎所有操作都是本地执行

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204250857650.png)

在 Git 中的绝大多数操作都**只需要访问本地文件和资源**，一般不需要来自网络上其它计算机的信息。

特性：

+ 断网后依旧可以在本地对项目进行版本管理
+ 联网后，把本地修改的记录同步到云端服务器即可





### 3.  Git 中的三个区域

使用 Git 管理的项目，拥有三个区域，分别是工作区、暂存区、Git 仓库。

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204250901307.png)





### 4. Git 中的三种状态

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204250902472.png)

注意：

+ 工作区的文件被修改了，但还没有放到暂存区，就是已修改状态。
+ 如果文件已修改并放入暂存区，就属于已暂存状态。 
+ 如果 Git 仓库中**保存着特定版本**的文件，就属于已提交状态。 





### 5. 基本的 Git 工作流程

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204250903434.png)

基本的 Git 工作流程如下：
在工作区中修改文件
将你想要下次提交的更改进行暂存
提交更新，找到暂存区的文件，将快照永久性存储到 Git 仓库





## Git 基础





### 1. 在 Windows 中下载并安装 Git

在开始使用 Git 管理项目的版本之前，需要将它安装到计算机上。可以使用浏览器访问如下的网址，根据自己的操作系统，选择下载对应的 Git [安装包](https://git-scm.com/downloads
)：

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204250921388.png)







### 2. 配置用户信息

安装完 Git 之后，要做的第一件事就是设置自己的**用户名**和**邮件地址**。因为通过 Git 对项目进行版本管理的时候，Git 需要使用这些基本信息，来记录是谁对项目进行了操作：

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204250921859.png)

注意：如果使用了 --global 选项，那么该命令只需要运行一次，即可永久生效 。





### 3. Git 的全局配置文件

通过 `git config --global user.name` 和 `git config --global user.email` 配置的用户名和邮箱地址，会被写入到 ==C:/Users/用户名文件夹/.gitconfig==文件中。这个文件是 Git 的**全局配置文件**，**配置一次即可永久生效**。

可以使用记事本打开此文件，从而查看自己曾经对 Git 做了哪些全局性的配置。







### 4. 检查配置信息

除了使用记事本查看全局的配置信息之外，还可以运行如下的终端命令，快速的查看 Git 的全局配置信息：

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204250926343.png)







### 5. 获取帮助信息

可以使用 git help <verb> 命令，无需联网即可在浏览器中打开帮助手册，例如：

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204250928169.png)

如果不想查看完整的手册，那么可以用 -h 选项获得更简明的“help”输出 ：

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204250931481.png)





### 6. 获取 Git 仓库的两种方式

+ **将**尚未进行版本控制的**本地目录转换为 Git 仓库**

+ 从其它服务器**克隆**一个已存在的 Git 仓库

以上两种方式都能够在自己的电脑上得到一个可用的 Git 仓库





### 7. 在现有目录中初始化仓库

如果自己有一个尚未进行版本控制的项目目录，想要用 Git 来控制它，需要执行如下两个步骤：

+ 在项目目录中，通过鼠标右键打开“Git Bash”
+ 执行 `git init` 命令将当前的目录转化为 Git 仓库

`git init` 命令会创建一个名为 `.git` 的隐藏目录，**这个 .git 目录就是当前项目的 Git 仓库**，里面包含了**初始的必要文件**，这些文件是 Git 仓库的**必要组成部分 **。





### 8. 工作区中文件的 4 种状态

工作区中的每一个文件可能有 4 种状态，这四种状态共分为两大类，如图所示：

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204250939222.png)









### 9. 检查文件的状态

可以使用 git status 命令查看文件处于什么状态，例如：

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204250950253.png)

在状态报告中可以看到新建的 **index.html** 文件出现在 **Untracked files**（未跟踪的文件） 下面。
未跟踪的文件意味着 **Git 在之前的快照（提交）中没有这些文件**；Git 不会自动将之纳入跟踪范围，除非明确地告诉它“我需要使用 Git 跟踪管理该文件”。





### 10. 以精简的方式显示文件状态

使用 git status 输出的状态报告很详细，但有些繁琐。如果希望以精简的方式显示文件的状态，可以使用如下两条完全等价的命令，其中 -s 是 --short 的简写形式：

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204250954612.png)

未跟踪文件前面有红色的 ?? 标记，例如：

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204250955844.png)







### 11. 跟踪新文件

使用命令 git add 开始跟踪一个文件。 所以，要跟踪 index.html 文件，运行如下的命令即可：

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204250955174.png)

此时再运行 git status 命令，会看到 index.html 文件在 Changes to be committed 这行的下面，说明已被跟踪，并处于暂存状态：

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204250959161.png)



![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204250959500.png)

以精简的方式显示文件的状态：
新添加到暂存区中的文件前面有绿色的 A 标记





### 12. 提交更新

现在暂存区中有一个 index.html 文件**等待被提交**到 Git 仓库中进行保存。可以执行 `git commit` 命令进行提交,其中 `-m` 选项后面是本次的**提交消息**，用来**对提交的内容做进一步的描述**：

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251000364.png)

提交成功之后，会显示如下的信息：

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251001828.png)

提交成功之后，再次检查文件的状态，得到提示如下：

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251003493.png)

证明工作区中所有的文件都处于“未修改”的状态，没有任何文件需要被提交。

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251003964.png)







### 13. 对已提交的文件进行修改

目前，index.html 文件**已经被 Git 跟踪**，并且**工作区和 Git 仓库**中的 index.html 文件**内容保持一致**。当我们修改了工作区中 index.html 的内容之后，再次运行 `git status` 和 `git status -s` 命令，会看到如下的内容：

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251007563.png)

文件 index.html 出现在 `Changes not staged for commit` 这行下面 ，说明**已跟踪文件的内容发生了变化**，**但还没有放到暂存区** 。

注意：修改过的、没有放入暂存区的文件前面有红色的 M 标记 。







### 14. 暂存已修改的文件

目前，工作区中的 index.html 文件已被修改，如果要暂存这次修改，需要再次运行 `git add` 命令，这个命令是个多功能的命令，主要有如下 3 个功效：

+ 可以用它**开始跟踪新文件**
+ 把**已跟踪的**、**且已修改的**文件放到暂存区
+ 把有冲突的文件标记为已解决状态

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251010036.png)





### 15. 提交已暂存的文件

再次运行 `git commit -m` "提交消息" 命令，即可将暂存区中记录的 index.html 的快照，提交到 Git 仓库中进行保存：

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251014666.png)

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251015157.png)







### 16. 撤销对文件的修改

撤销对文件的修改指的是：把对工作区中对应文件的修改，**还原**成 Git 仓库中所保存的版本。
操作的结果：所有的修改会丢失，且无法恢复！**危险性比较高**，**请慎重操作**！

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251018208.png)

撤销操作的本质：用 Git 仓库中保存的文件，覆盖工作区中指定的文件。命令是 git checkout -- 注意 是减号





### 17. 向暂存区中一次性添加多个文件

如果需要被暂存的文件个数比较多，可以使用如下的命令，一次性将所有的新增和修改过的文件加入暂存区：

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251045571.png)

今后在项目开发中，会经常使用这个命令，将新增和修改过后的文件加入暂存区。





### 18. 取消暂存的文件

如果需要从暂存区中移除对应的文件，可以使用如下的命令：

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251049405.png)





### 19. 跳过使用暂存区域

Git 标准的工作流程是==工作区 → 暂存区 → Git 仓库==，但有时候这么做略显繁琐，此时可以跳过暂存区，直接将工作区中的修改提交到 Git 仓库，这时候 Git 工作的流程简化为了==工作区 → Git 仓库==。
Git 提供了一个跳过使用暂存区域的方式， 只要在提交的时候，给 `git commit` 加上` -a `选项，Git 就会自动把所有已经跟踪过的文件暂存起来一并提交，从而跳过 git add 步骤 ：

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251056757.png)





### 20. 移除文件

从 Git 仓库中移除文件的方式有两种：

+ 从 Git 仓库和工作区中**同时移除**对应的文件
+ 只从 Git 仓库中移除指定的文件，但保留工作区中对应的文件

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251100649.png)





### 21. 忽略文件

一般我们总会有些文件无需纳入 Git 的管理，也不希望它们总出现在

未跟踪文件列表。 在这种情况下，我们可以创建一个名为 

`.gitignore` 的配置文件，列出要忽略的文件的匹配模式。

文件 .gitignore 的格式规范如下：

以 **# 开头**的是注释

以 **/ 结尾**的是目录

以 **/ 开头**防止递归

以 **! 开头**表示取反

可以使用 **glob 模式**进行文件和文件夹的匹配（glob 指简化了的正则

表达式）





### 22.  glob 模式

所谓的 **glob 模式**是指简化了的正则表达式：

 **星号 *** 匹配**零个或多个任意字符**

**[abc]** 匹配**任何一个列在方括号中的字符** （此案例匹配一个 a 或

匹配一个 b 或匹配一个 c）

 **问号 ?** 只**匹配一个任意字符**

 在方括号中使用**短划线**分隔两个字符， 表示所有在这两个字符范围

内的都可以匹配（比如 [0-9] 表示匹配所有 0 到 9 的数字）

 **两个星号 **** 表示**匹配任意中间目录**（比如 a/**/z 可以匹配 a/z 、 

a/b/z 或 a/b/c/z 等）





### 23. .gitignore 文件的例子

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251112729.png)





### 24. 查看提交历史

如果希望回顾项目的提交历史，可以使用 `git log` 这个简单且有效的命令。

按q退出查看历史

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251128654.png)





### 24. 回退到指定的版本

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251139329.png)







## GitHub





### 1. 什么是开源

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251301329.png)





### 2. 什么是开源许可协议

开源并不意味着完全没有限制，为了**限制使用者的使用范围**和**保护作者的权利**，每个开源项目都应该遵守**开源许可协议**（ Open Source License ）。





### 3. 常见的 5 种开源许可协议

+ BSD（Berkeley Software Distribution）

+ Apache Licence 2.0

+ ` GPL`（GNU General Public License）
  具有传染性的一种开源协议，不允许修改后和衍生的代码做为闭源的商业软件发布和销售
  使用 GPL 的最著名的软件项目是：Linux

+  LGPL（GNU Lesser General Public License）

+ ` MIT`（Massachusetts Institute of Technology, MIT）
  是目前限制最少的协议，唯一的条件：在修改后的代码或者发行包中，必须包含原作者的许可信息
  使用 MIT 的软件项目有：jquery、Node.js

  关于更多开源许可协议的介绍，可以参考博客 https://www.runoob.com/w3cnote/open-source-license.html





### 4. 为什么要拥抱开源

开源的**核心思想**是“我为人人，人人为我”，人们越来越喜欢开源大致是出于以下 3 个原因：
开源给使用者更多的控制权
开源让学习变得容易
开源才有真正的安全

开源是软件开发领域的大趋势，拥抱开源就像站在了巨人的肩膀上，不用自己重复造轮子，让开发越来越容易。





### 5. 开源项目托管平台

专门用于免费存放开源项目源代码的网站，叫做开源项目托管平台。

目前世界上比较出名的开源项目托管平台主要有以下 3 个：

+ Github（全球最牛的开源项目托管平台，没有之一）
+ Gitlab（对代码私有性支持较好，因此企业用户较多）
+ Gitee（又叫做**码云**，是国产的开源项目托管平台。访问速度快、纯中

文界面、使用友好）

注意：以上 3 个开源项目托管平台，只能托管以 Git 管理的项目源代

码，因此，它们的名字都以 Git 开头。





### 6. 什么是 Github

Github 是全球最大的**开源项目托管平台**。因为只支持 Git 作为唯一的

版本控制工具，故名 GitHub。

在 Github 中，你可以：

关注自己喜欢的开源项目，为其点赞打 call 

为自己喜欢的开源项目做贡献（Pull Request）

和开源项目的作者讨论 Bug 和提需求 （Issues）

把喜欢的项目复制一份作为自己的项目进行修改（Fork）

创建属于自己的开源项目

etc…

So，**Github ≠ Git**





### 7. 注册 Github 账号的流程

+ 访问 Github 的官网首页 https://github.com/
+ 点击“Sign up”按钮跳转到注册页面
+ 填写可用的用户名、邮箱、密码
+ 通过点击箭头的形式，将验证图片摆正
+ 点击“Create account”按钮注册新用户
+ 登录到第三步填写的邮箱中，点击激活链接，完成注册

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251503180.png)

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251503807.png)





### 8. 激活 Github 账号

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251504030.png)

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251505774.png)







### 9. 完成注册

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251506832.png)





### 10. 远程仓库的使用





#### ① 新建空白远程仓库

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251507473.png)







#### ② 新建空白远程仓库成功

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251507521.png)





#### ③ 远程仓库的两种访问方式

Github 上的远程仓库，有两种访问方式，分别是 `HTTPS` 和 `SSH` 。它

们的区别是：

+ HTTPS ：**零配置**；但是每次访问仓库时，需要重复输入 Github 的

  账号和密码才能访问成功

+ SSH ：**需要进行额外的配置**；但是配置成功后，每次访问仓库

  时，不需重复输入 Github 的账号和密码

注意：在实际开发中，**推荐使用 SSH 的方式访问远程仓库**。





#### ④ 基于 HTTPS 将本地仓库上传到 Github

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251521336.png)

第一次之后只需要用 git push 就能直接上传本地 git 仓库了





#### ⑤ SSH key

SSH key 的**作用**：实现本地仓库和 Github 之间免登录的加密数据传

输。

SSH key 的**好处**：免登录身份认证、数据加密传输。

SSH key 由**两部分组成**，分别是：

+ id_rsa（私钥文件，存放于客户端的电脑中即可）
+ id_rsa.pub（公钥文件，需要配置到 Github 中）







#### ⑥ 生成 SSH key

打开 Git Bash

粘贴如下的命令，并将 your_email@example.com 替换为注册 Github 

账号时填写的邮箱：

+ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

连续敲击 3 次回车，即可在 ==C:\Users\用户名文件夹\.ssh== 目录中生成 

`id_rsa` 和 `id_rsa.pub` 两个文件





#### ⑦  配置 SSH key

使用记事本打开 `id_rsa.pub` 文件，复制里面的文本内容

在浏览器中登录 Github，==点击头像 -> Settings -> SSH and GPG Keys -> New SSH key==

将 id_rsa.pub 文件中的内容，==粘贴到 Key 对应的文本框中==

在 Title 文本框中任意填写一个名称，来标识这个 Key 从何而来







#### ⑧ 检测 Github 的 SSH key 是否配置成功

打开 Git Bash，输入如下的命令并回车执行：

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251554158.png)

上述的命令执行成功后，可能会看到如下的提示消息：

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251554274.png)

输入 yes 之后，如果能看到类似于下面的提示消息，证明 SSH key 已经配置成功了

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251555913.png)

注意 ：严格区分大小写





#### ⑨ 基于 SSH 将本地仓库上传到 Github

![](https://cdn.jsdelivr.net/gh/Nhenk/Nhenk-repository/202204251601087.png)





## Git 分支











