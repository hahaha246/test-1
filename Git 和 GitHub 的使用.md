# 一、使用[Github](https://so.csdn.net/so/search?q=Github&spm=1001.2101.3001.7020)



## 1.目的

​	借助github托管项目代码。



## 2.基本概念

#### 	（1）.仓库（Repository）

​		仓库：即你的项目，想在Github上开源一个项目，那就必须要新建一个Repository，如果你开源项目多了，你就拥有多个Repositories。

#### 	（2）.收藏（Star）

​		仓库主页star按钮，意思为收藏项目的人数，在Github上如果你有一个项目获得100个star都算很不容易了！

#### 	（3）.复制克隆项目（Fork）

​		这个不好翻译，如果实在要翻译，我把他翻译成分叉，什么意思呢？你开源了一个项目，别人想在你这个项目的基础上做些改进，然后应用到自己的项目中，这个时候他就可以Fork你的项目（打开项目主页点击右上角的fork按钮即可），然后他的GitHub主页上就多了一个项目，只不过这个项目是基于你的项目基础（本质上是在原有项目的基础上新建了一个分支），他就可以随心所欲的去改进，但丝毫不会影响原有项目的代码和结构。

#### 	（4）.发起请求（Pull Request）

​		发起请求，这个其实是基于Fork的，如果别人在你的基础上做了改进，后来觉得改进的很不错，应该要把这些改进让更多的人受益，于是就想把自己的改进合并到原有的项目里，这时候他就可以发起一个Pull Request（简称PR），原有项目创建人，也就是你，就可以收到这个请求，这个时候你会仔细review他的代码，并且测试觉得ok了，就会接受他的PR，这个时候他做的改进原有项目就会有了。

#### 	（5）.关注（Watch）

​		这个也好理解就是观察，如果你Watch了某个项目，那么以后只要这个项目有任何更新，你都会第一时间收到关于这个项目的通知提醒了。

#### 	（6）.事务卡片（Issue）

​		发现代码Bug，但是目前没有成型代码，需要讨论使用；

​		问题的意思，举个例子，就是你开源了一个项目，别人发现你的项目中有bug，或者那些地方做的不够好，他就可以给你提一个Issue，提的问题多了也就是Issues，然后你看到这些问题就可以逐一去修复，修复ok了你就可以一个个Close掉。

#### 	（7）.Github主页

​		装好创建成功或者点击网址导航栏github图标都可以进入github主页：该页左侧主要显示用户动态以及关注用户或关注仓库的动态；右侧显示所有的git库

#### 	（8）.仓库主页

​		仓库主页主要显示项目的信息，如：项目代码，版本，收藏/关注/fork情况等。

#### 	（9）.个人主页

​		个人信息：头像，个人简介，关注我的人，我关注的人，我关注的git库，我的开源项目，我贡献的开源项目等信息。





# 二、Git



## 1.Git的安装

1. 下载、安装git

```
https://git-scm.com/downloads
```

2. 在终端输入 `git --version` 查看版本信息 。

```
git --version
```

![[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-8zDg2UVz-1609345795563)(/Users/mac/Desktop/前端学习笔记/git笔记/git笔记一/14.jpg)]](https://img-blog.csdnimg.cn/20201231003429799.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjM1MTU5Mw==,size_16,color_FFFFFF,t_70#pic_center)

## 2.Git的配置

1. 创建一个全局用户名、全局邮箱作为配置信息。

```
git config --global user.name "your_name"  
git config --global user.email "your_email@youremail.com"
```

2. 配置信息可以更改，以后想要更改，使用上面指令就可以。

   同时可以使用`git config --list`指令查看Git的配置信息。

```
git config --list
```

![[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-H870dLww-1609345795564)(/Users/mac/Desktop/前端学习笔记/git笔记/git笔记一/15.gif)]](https://img-blog.csdnimg.cn/20201231003445660.gif#pic_center)

按q退出。

3. Git默认对大小写不敏感，也就是说，将一个文件名某个字母做了大小写转换的修改Git是忽略这个改动的，导致在同步代码时候会出现错误，所以建议把Git设置成大小写敏感。

```git
git config core.ignorecase false
```

4. 生成密匙

- Git关联远端仓库时候需要提供公钥，本地保存私钥，每次与远端仓库交互时候，远端仓库会用公钥来验证交互者身份。
- 使用以下指令生成密钥，如果有提示，一路点击回车。

```css
ssh-keygen -t rsa -C "your_email@youremail.com"
```

- 生成密钥后，在本地的`/Users/mac/.ssh`目录下会生成两个文件id_rsa、id_rsa.pub
  - id_rsa文件保存的是私钥，保存于本地
  - id_rsa.pub文件保存的是公钥，需要将里面内容上传到远端仓库。

5. **获取密匙字符串**
   - 输入cat /Users/mac/.ssh/id_rsa.pub指令，查看id_rsa.pub文件中内容

6. 打开你的github账号，在`Settings`中的左侧边导航中找到`SSH and GPG keys`，点击左面面板右上方的`New SSH key`添加密匙。![[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-FNJqCUGe-1609345795565)(/Users/mac/Desktop/前端学习笔记/git笔记/git笔记一/16.jpg)]](https://img-blog.csdnimg.cn/20201231003503619.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjM1MTU5Mw==,size_16,color_FFFFFF,t_70#pic_center)



## 3.Git工作区域

### 	(1). 工作区（Working Directory）

​			添加、编辑、修改文件等动作。

### 	(2). 暂存区

​			暂存已经修改的文件最后统一提交到git仓库中。

### 	(3). Git Repository（Git 仓库）

​			最终确定的文件保存到仓库，成为一个新的版本，并且对他人可见。





## 4.初始化一个新的Git仓库

### 	(1). 本地创建文件夹

```
mkdir test
```

### 	(2). 在文件夹内初始化Git（创建Git仓库）

```
cd test
git init
```

![[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-4TtxtG9X-1609345795566)(/Users/mac/Desktop/前端学习笔记/git笔记/git笔记一/17.jpg)]](https://img-blog.csdnimg.cn/20201231003518574.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjM1MTU5Mw==,size_16,color_FFFFFF,t_70#pic_center)

### (3). 向仓库中添加文件

1. **创建文件**

```
touch a1.js
```

![[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-rJmE6JA1-1609345795567)(/Users/mac/Desktop/前端学习笔记/git笔记/git笔记一/18.jpg)]](https://img-blog.csdnimg.cn/20201231003530221.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjM1MTU5Mw==,size_16,color_FFFFFF,t_70#pic_center)

（可用`git status`检查状态）

2. **将文件提交到暂存区**

```
git add a1.js
```

![[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-k0zlhzlt-1609345795568)(/Users/mac/Desktop/前端学习笔记/git笔记/git笔记一/19.jpg)]](https://img-blog.csdnimg.cn/20201231003541465.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjM1MTU5Mw==,size_16,color_FFFFFF,t_70#pic_center)

3. **将文件提交到git仓库**

```
git commit -m "add a1.js"
```

![[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-k94RqeKE-1609345795569)(/Users/mac/Desktop/前端学习笔记/git笔记/git笔记一/20.jpg)]](https://img-blog.csdnimg.cn/2020123100355310.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjM1MTU5Mw==,size_16,color_FFFFFF,t_70#pic_center)

### (4). 删除文件

1. 删除文件

```
rm a1.js
```

2. 从Git中删除文件

```
git rm a1.js
```

3. 提交操作

```
git commit - m "提交描述"
```

![[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-LdzCsK69-1609345795570)(/Users/mac/Desktop/前端学习笔记/git笔记/git笔记一/21.jpg)]](https://img-blog.csdnimg.cn/20201231003612348.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjM1MTU5Mw==,size_16,color_FFFFFF,t_70#pic_center)



## 5.Git管理远程仓库

### 	(1). 将远程仓库克隆下来

```git
git clone 仓库地址
```

![[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-wvR8Sjc6-1609345795571)(/Users/mac/Desktop/前端学习笔记/git笔记/git笔记一/22.jpg)]](https://img-blog.csdnimg.cn/20201231003624272.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjM1MTU5Mw==,size_16,color_FFFFFF,t_70#pic_center)

### 	(2). 在本地工作区中创建文件

![[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-FVE7D8iB-1609345795571)(/Users/mac/Desktop/前端学习笔记/git笔记/git笔记一/23.jpg)]](https://img-blog.csdnimg.cn/20201231003636746.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjM1MTU5Mw==,size_16,color_FFFFFF,t_70#pic_center)

### 	(3). 将该文件提交到远程仓库

1. 提交到暂存区

```git
git add a1.js
```

2. 提交到本地仓库

```git
git commit -m "提交说明"
```

3. 提交到远程仓库

```
git push
```



# 三、Git增强

### [diff-so-fancy](https://github.com/so-fancy/diff-so-fancy)

![diff so fancy 截图](https://github.phodal.com/chapter/img/git-diff-screenshot.png)

### [git-extras](https://github.com/tj/git-extras)