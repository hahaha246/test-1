### 1 Sourcetree介绍

Sourcetree是一款免费的Git图形化客户端，它由Atlassian开发，提供了跨平台的支持，可运行在Windows和Mac操作系统上。Sourcetree可以让开发者更方便地使用Git来管理代码，不需要在命令行中输入复杂的[Git命令](https://so.csdn.net/so/search?q=Git命令&spm=1001.2101.3001.7020)，而是通过可视化的界面完成代码管理操作。

Sourcetree支持多种Git工作流，例如Git Flow、GitHub Flow等，可以帮助开发者更好地管理Git分支、合并代码、提交代码等操作。此外，Sourcetree还集成了一些实用的功能，例如自动提交、撤销提交、文件比较、文件历史记录等，方便开发者进行代码管理和版本控制。

总的来说，Sourcetree是一款易于使用的Git客户端，它的图形化界面使得Git操作更加直观和简单，适合那些不熟悉Git命令行的初学开发者，当然是太适合我啦~

- https://sourcetreeapp.com/

![图1.1 Sourcetree下载](https://img-blog.csdnimg.cn/img_convert/5380f4261cfa887078fa08c3b639a47e.png)

```
当然也可通过我分享的链接下载，如有需要可访问下方链接进行下载v3.4.12版本。
```

> 阿里云盘下载 https://www.aliyundrive.com/s/Q6JnuYanfCm
> 提取码: 53kv

### 2 安装简明教程

- 1） 双击安装文件，出现如下界面，可以选择跳过

![img](https://img-blog.csdnimg.cn/img_convert/4d0017696d7bbfc8464e2f1dc872b629.png)

- 2）如果之前安装过Git，则是下面的界面：

![img](https://img-blog.csdnimg.cn/img_convert/88536bba9a9794f64f48c01104e7a563.png)

如果系统之前没有安装Git，这里会自动勾选Git，如下所示：

![img](https://img-blog.csdnimg.cn/img_convert/035892480f4cdf0add8236af7d2684f0.png)

```
这里的，Mercurial也是一种用于软件开发的分布式版本控制系统，也可不选，用Git就好了
```

![img](https://img-blog.csdnimg.cn/img_convert/2d52e0ce3d024c2ebdcdc475d2ab0919.png)

![img](https://img-blog.csdnimg.cn/img_convert/1a7a27555507a3d4f72a80026137f391.png)

- 3）配置首选项

![img](https://img-blog.csdnimg.cn/img_convert/f316a7e34602c3b37f85d7307afaa2c4.png)

- 4）选择是否创建SSH密钥，可以后面再配置，我先选择否吧

![img](https://img-blog.csdnimg.cn/img_convert/d0b0c04d96731117d23b86b63a154127.png)

- 5）完成安装

![img](https://img-blog.csdnimg.cn/img_convert/460601eb59627026cde906e91cd26efa.png)

### 3 软件基本配置

#### 3.1 生成密钥

```
如果你之前使用Git生成过SSH密钥,可直接跳至3.2节
```

1）打开Git Bash输入以下命令，记得更加最后一个参数（邮箱），接下来一路回车即可。

```bash
ssh-keygen -t rsa -C "xxxxx@xxxxx.com"
1
```

![img](https://img-blog.csdnimg.cn/img_convert/aaecfac89720685b8c407832accdfb54.png)

2）输入以下命令,找到生成密钥值的目录,前往.ssh目录、查看对应的公钥

```bash
cat ~/.ssh/id_rsa.pub
1
```

![img](https://img-blog.csdnimg.cn/img_convert/5bbdda54f47a0aa8f0943b88b333531e.png)

![img](https://img-blog.csdnimg.cn/img_convert/916208d78d0c709102805694afc8437c.png)
3）输入以下命令，来查看是否成功，若出现“successfully”字段则表示成功！

```bash
ssh -T git@github.com
1
```

![img](https://img-blog.csdnimg.cn/img_convert/613001779a74881d3cad08aaee80949d.png)

#### 3.2 参数配置

输入3.1节生成的密钥文件路径到相应框即可，具体可按照下图操作。`密钥文件一般就放在用户目录下.ssh文件夹里面。`如果实在找不到id_isa文件，还是去百度百度吧~

![img](https://img-blog.csdnimg.cn/img_convert/acaeaa603bb802ddfe5a0d94a742ea7c.png)

### 4 基本使用教程

#### 4.1 创建一个本地仓库

1）在本地创建一个仓库
![img](https://img-blog.csdnimg.cn/img_convert/4b69be3c1323001d9b476a534bb464bd.png)

2）在github上面同样也创建一个远程仓库
![img](https://img-blog.csdnimg.cn/img_convert/d9aead8e867205c2d7e254134c56e049.png)

3）设置本地仓库，使之关联到远程仓库
![img](https://img-blog.csdnimg.cn/img_convert/6efca747877426880a0a2b3d00fd54bc.png)

！！如果使用ssh协议就在 **url/路径** 里面填写ssh协议下的地址，如果采用 **https协议** 就填写https协议下的地址，这里我以https协议为例，如下图所示。
其中ssh协议不需要用户名和密码，只需要**配置公钥**即可，而ssh协议依托于账户的**用户名和密码**。

![img](https://img-blog.csdnimg.cn/img_convert/12bad281e090dd9777c644dcb3a519ee.png)

4）我们在本地仓库中新建一个main.cpp文件，返回Sourcetree出现了未暂存文件；

![img](https://img-blog.csdnimg.cn/img_convert/71b2c9108640a8cab73b7155e2e53335.png)

5）暂存所有文件或部分文件，填入相应的commit信息，并提交修改；

![img](https://img-blog.csdnimg.cn/img_convert/b0f49d6b556159a905783d8ab6e5293b.png)

6）完成之后，我们通过`推送`按钮将修改推送到远端；

![img](https://img-blog.csdnimg.cn/img_convert/d112b6db26ac797048e0f65b73207444.png)

7）首次进行推送，可能需要验证账户，按下面的操作即可；

![img](https://img-blog.csdnimg.cn/img_convert/4b7219f4f09840ba30d58c7dcd677e3e.png)

8）提交成功之后，我们就可以在github远端出现修改的文件；

![img](https://img-blog.csdnimg.cn/img_convert/667b42061b34874a2c3082a5d055b565.png)

#### 4.2 添加一个本地仓库

`添加一个本地仓库还是相对容易一些`
![img](https://img-blog.csdnimg.cn/img_convert/f7644a0aaca2223fc70f0a4e2ea66c55.png)

#### 4.3 克隆一个远程仓库

1)复制远程仓库的路径地址;
![img](https://img-blog.csdnimg.cn/img_convert/a59f0815586e2db94aa35a8a7330fdc1.png)

2）添加之后，软件会主动去检查路径是否合法，填写克隆到本地的信息之后点击`克隆`即可.
![img](https://img-blog.csdnimg.cn/img_convert/eaaf6d65b5c91c05153293ccc3bda6f0.png)

### 5 结束语

总的来说，Sourcetree是一款功能强大且易于使用的Git图形化客户端，可以帮助开发者更方便地使用Git来管理代码，提高开发效率和代码质量。

这次就先写这么多吧，基本的使用应该是没有问题啦~当然了这里只是介绍了一些基础操作，更复杂的软件操作过程就等各位小伙伴自行探索啦，后面有机会我再更新一些常用的内容吧。

感谢各位小伙伴们的关注，起风了，唯有努力生存~

![img](https://img-blog.csdnimg.cn/img_convert/1d9515cdb8d230cbc8cd3b59c18489ec.jpeg)