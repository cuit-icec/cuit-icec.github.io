欢迎电协的每一位同学加入到这个 Wiki 的编辑中来，让大家的知识更加集中。

## 前提

你需要注册一个 GitHub 账号，[注册新 GitHub 帐户 - GitHub Docs](https://docs.github.com/cn/github/getting-started-with-github/signing-up-for-a-new-github-account).

## 修改编辑

在参与 Wiki 的编写 **需要** 一个 GitHub 账号，**但不需要** 高超的 GitHub 技巧。

假如我想要修改一个页面内容，应该怎么操作呢？

1. 在 **ICEC Wiki** 网站上找到对应页面；
2. 点击正文右上方、目录左侧的 **“编辑此页”** *edit* 按钮；
3. 在编辑框里编写你想修改的内容。另外，由于 **ICEC Wiki** 使用 Markdown 进行编写，如果想进行一些比较大的更改（比如扩充页面内容），你需要掌握一些 [Markdown 语法](https://markdown.tw/) ；
4. 写好了之后点下方的绿色按钮 Propose changes 提交修改。但是，GitHub 可能会提示你没有权限。不必担心！GitHub 会自动帮你将 **ICEC Wiki** 的所有文件复制一份，放到你的仓库中（fork）并创建申请合并更改的请求 (Pull Request)；
5. 之后，点上方的绿色按钮 (Create pull request) 后，GitHub 会跳转到一个新的页面 Open a pull request。删掉方框里的文字，简单写写你做的修改，然后再点一下下面的绿色按钮 (Create pull request)；
6. 不出意外的话，你的 PR 就顺利提交到仓库，等待合并了。之后，你就可以等待项目组合并你的分支，或者指出还要修改的地方。当然，你也可以给他人的 PR 提出修改意见，或者只是点赞/踩。如果有消息，会有邮件通知和/或出现在网页右上角的提醒（取决于你个人 Settings 中的设置）。

## 加入维护队伍（选取一小块内容负责管理）

联系当前网站管理：[钟弋辰](https://github.com/ActivePeter)，[谭丰伟](https://github.com/tfx2001)，我们会将你加入到仓库的开发者中。

## 文章中涉及图片

这里的话，有两种方式：

1. 将图片放入 `_static/images` 中，这种方式需要将项目 clone 下来，具体看 [clone到本地编辑](#_5) ；
2. （待补充）。

## clone到本地编辑

把项目 **clone** 下来可以更灵活的编辑内容，如 **图片，目录结构，新增文章** 等。

考虑到有不熟悉或不了解 Git 的同学，我们将给出一套 **最容易入门，不容易出错** 的完整方案。

### 1.[安装 Git](../../tool/manage/git.md)；

### 2.[安装新手友好的图形化 Git 界面 - Sourcetree](../../tool/manage/sourcetree.md)；

### 3.clone wiki仓库

先在本地找好要clone的文件夹，然后在该文件夹内右键，打开![image-20210204002242363](https://gitee.com/zhongyichen33/testtupian/raw/master/20210204002242.png)，然后输入以下语句：`git clone https://hub.fastgit.org/cuit-icec/cuit-icec.github.io.git`

执行完后，项目就已经克隆到你的本地了，**如果感觉放的位置不对，迁移这个文件夹也是可以的**

然后去sourcetree中打开这个文件夹，

可以看到内容的**提交记录**

![image-20210204002813871](https://gitee.com/zhongyichen33/testtupian/raw/master/20210204002813.png)

还有顶栏里的**常用操作**

![image-20210204002909114](https://gitee.com/zhongyichen33/testtupian/raw/master/20210204002909.png)

### 4.[安装typora](../../../tool/note/markdown/typora/)

### 5.编写文章

使用typora打开项目**根目录中的readme.md**

![image-20210204005619174](https://gitee.com/zhongyichen33/testtupian/raw/master/20210204005619.png)

大概看到的界面是这样的，然后就可以**开始编写**了

如果侧边栏不是树形结构，建议**切换成树形结构**

在侧边栏底部的右边![image-20210204005754508](https://gitee.com/zhongyichen33/testtupian/raw/master/20210204005754.png)

### [6.安装vscode](../../tool/software/code_editor/visual_studio_code)

### 7.变动目录结构，添加文章

1.使用vscode打开我们的项目文件夹

(右键文件夹空白处->通过vscode打开，或vscode -> 文件 -> 打开文件夹）

2.选择mkdocs.yml,我们需要通过修改这个文件来进行目录的变更还有文章的添加，

格式很简单，其实看文件现有的内容就大概能明白

![image-20210204014812545](https://gitee.com/zhongyichen33/testtupian/raw/master/20210204014812.png)

`- Home: index.md`相当于网页侧边栏直接指向一个文章页面，Home对应的栏目名称，index.md对应的在docs文件夹中的相对路径

![image-20210204015002101](https://gitee.com/zhongyichen33/testtupian/raw/master/20210204015002.png)

```
- 参与 Wiki 的贡献: 
      - 如何参与贡献: icec/contri/howto.md
      - 当前人员分配: icec/contri/member.md
```

这样一个格式相当于形成了二级目录，

**<u>注意：</u>**

1.只写一句`- 参与 Wiki 的贡献: `而后面既不跟文件名，又不跟二级目录**是不行的，会报错的**！

2.**横线**后面需要有**空格**，然后如果是指向文件**冒号**后面需要有**空格**

3.新建的md文件名最好是**英文**。因为路径会跟网页路径一致，中文的网页路径会变得又臭又长

### 8.在本地预览效果

这一步是用来确认**效果是否让你满意**和**排查问题**的，**可以[跳到下一步](#9)**

### 9.提交文章

1、打开**sourcetree**，左边侧边栏点选到**文件状态**，我们可以看到改动的文件会罗列在为暂存文件夹中

![image-20210204022132477](https://gitee.com/zhongyichen33/testtupian/raw/master/20210204022132.png)

2.点击**暂存所有**，在下放栏目中写上**简略的注释**，点击**提交**

![image-20210204022403436](https://gitee.com/zhongyichen33/testtupian/raw/master/20210204022403.png)

3.一般来说当前是**最新的分支状态**的话，直接就**[顺利提交](#10github-action)**了

4.有些时候可能会提交不成功，因为不是最新的，![image-20210204022617940](https://gitee.com/zhongyichen33/testtupian/raw/master/20210204022618.png)拉取有数字，那么我们需要**先拉取**一下，以同步最新的commit，**然后提交**，一般来说，没有**冲突**的话，这一步就**[顺利提交](#10github-action)**了

5.最坏的一种情况，出现了**冲突**（**本地的改动**和**最新的commit的改动**在同一个地方进行了修改）

如图：

这种时候我个人觉得最方便的解决办法是进**vscode**里，然后查看冲突文件（vscode会把**冲突文件**标记成**紫色**的

然后会在**冲突的位置**显示出两个版本的内容，我们**根据内容进行选取**就行，如果暂时无法确定舍弃哪一部分，就选择**两者都保留**，

这样操作之后，回到sourcetree里，保存未暂存文件，会发现里面的冲突不见了，下面的描述框里面会有一大段英文描述自动帮你写好了，然后我们进行一次提交和推送，**冲突解决，[提交成功](#10github-action)。**

### 10.顺利提交，等待github action部署

[去github查看部署进度](https://github.com/cuit-icec/cuit-icec.github.io/actions)

部署完成后刷新对应的页面就能看到变更啦~