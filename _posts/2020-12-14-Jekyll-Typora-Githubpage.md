---
layout: post
title:  "用Jekyll,Typora和Github Page搭建个人博客"
date:   2020-12-14 23:41:00 +0800
categories: jekyll update
---

## 使用SSH连接到GitHub

1. 生成SSH密钥

```
ssh-keygen -t ed25519 -C "m15737740589@163.com"
```

2. 在后台启动 ssh 代理

```
eval "$(ssh-agent -s)"
```

3. 将 SSH 私钥添加到 ssh-agent

```
ssh-add ~/.ssh/id_ed25519
```

4. 将 SSH 密钥复制到剪贴板

   ```
   sudo apt-get install xclip
   xclip -selection clipboard < ~/.ssh/id_ed25519.pub
   ```

5. 在任何页面的右上角，单击您的个人资料照片，然后单击 Settings（设置），在用户设置侧边栏中，单击 SSH and GPG keys（SSH 和 GPG 密钥），单击 New SSH key（新 SSH 密钥）或 Add SSH key（添加 SSH 密钥），在 "Title"（标题）字段中，为新密钥添加描述性标签，将密钥粘贴到 "Key"（密钥）字段，单击 Add SSH key（添加 SSH 密钥）。

6. 使用以下命令来测试是否成功

   ```
   ssh -T git@github.com
   ```

## 安装Git

```
sudo apt install git
git config --global user.name "Xingshihao"
git config --global user.email m15737740589@163.com
git init
#已初始化空的 Git 仓库于 /home/xsh/.git/
```

## 安装Jekyll

```
sudo apt-get install ruby-full build-essential zlib1g-dev
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
gem install jekyll bundler
gem install jekyll bundler
jekyll new myblog
cd myblog
bundle exec jekyll serve
```

## 申请Github page

1. 新建一个rop，仓库名称有固定的格式： username.github.io，其中username必须是Github账户的用户名（我的是FollowHeart007），http://github.io是固定的，这个地址将会成为个人站点的网站地址。另外，我们可以勾选Initialize this repository with a README，让仓库自动创建一个README.md文件，我们用它来做站点的首页（当然也可以不创建，后面自行创建，或是建立index.html也行）。

   注意： username如果不是Github账户名，这个仓库就会成为username.github.io的子站点，比如访问地址会是：username.github.io/aaa.github.io。可见，username.github.io是Github默认分配给你的域名，同名仓库即代表着默认网站内容。而username.github.io/仓库名称，是用来访问你的其它仓库的地址。

2. 后续过程可以参考知乎的这篇文章

   [知乎]: https://zhuanlan.zhihu.com/p/51240503

3. 使用命令将自己和别人的博客主题克隆到本地

   ```
   git clone git@github.com:leopardpan/leopardpan.github.io.git
   git clone git@github.com:FollowHeart007/FollowHeart007.github.io.git
   ```

4. 将FollowHeart007.github.io文件夹里面的内容全部替换成leopardpan.github.io里面的内容。

5. 对FollowHeart007.github.io里面的内容进行修改，详细可以参考Bilibili这两个视频

   [借鉴他人主题]: https://www.bilibili.com/video/BV14x411t7ZU?from=search&amp;seid=14765380962892041632
   [基本构建步骤]: https://www.bilibili.com/video/BV1rC4y1878Y?from=search&amp;seid=14765380962892041632

## 安装Typora

```
sudo apt-get install typora
```

## 使用Git将本地仓库上传

1. 使用命令在本地预览仓库

   ```
   jekyll server
   ```

   

2. 使用Git将本地仓库上传到网上

```
git add .
git commit -m "init"
git push origin
```

