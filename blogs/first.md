---
title: Vuepress搭建个人博客教程
date: 2020-06-21
tags:
 - Vue
 - 生活
categories:
 - 教程
---

<!-- more -->

# VuePress介绍

VuePress是尤雨溪18年4月12日发布的vue静态网站生成器，支持vue语法，内置webpack，每一个由vuepress生成的页面都是通过SSR预渲染的HTML，也因此具有非常好的加载性能和搜索引擎优化。

因为VuePress允许在MarkDown中插入Vue组件，非常适合用来做项目文档，例如自己的组件库文档

而且现在越来越多的人用来写博客，这次文章就是一个简单的使用教程和主题推荐

使用VuePress之前请确保你本地的node环境

VuePress不限于使用markdown、vue组件、html

[VuePress官方文档](https://vuepress.vuejs.org/zh/)


# reco主题

[reco主题](https://vuepress-theme-reco.recoluan.com/)

推荐这款主题的原因，是因为reco主题提供了脚手架可以实现一键创建vuepress项目。

#快速开始
npx

```powershell
npx @vuepress-reco/theme-cli init my-blog
```

npm

```powershell
# 初始化

npm install @vuepress-reco/theme-cli -g
theme-cli init my-blog

# 安装

cd my-blog
npm install

# 运行

npm run dev

# 编译

npm run build
```


yarn

```powershell
# 初始化

yarn global add @vuepress-reco/theme-cli
theme-cli init my-blog

# 安装

cd my-blog
yarn install
```



# 创建第一遍文章

进入到my-blog目录中，使用 `npm i`命令下载一下依赖

打开 `my-blog\docs\.vuepress\config.js`,配置一些自定义信息，具体的可配置信息[立即前往](https://vuepress-theme-reco.recoluan.com/views/1.x/configJs.html)

在`blogs`目录下新建一个 `first.md` 文件，这个前面的内容相当于是文章的信息描述，具体的可描述信息[立即前往](https://vuepress-theme-reco.recoluan.com/views/1.x/frontMatter.html)

```markdown
---
title: 这是我的第一个文章
date: 2020-05-15
sidebar: 'auto'
categories:
 - 博文
tags:
 - 日常
---

## 这是我的第一篇文章
```

然后使用 `npm run dev`将项目运行起来

### 可以给文章添加摘要

```markdown
---
title: 这是我的第一个文章
date: 2020-05-15
sidebar: 'auto'
categories:
 - 博文
tags:
 - 日常
---

::: tip
你好
:::
<!-- more -->

## 这是我的第一篇文章
```

`<!-- more -->` 标签前的内容会被作为文章摘要与文章的信息描述一起展示，之后的内容则需要打开文章进行查看。

# 部署

先在GitHub上新建一个名为 `你的用户名.github.io` 的仓库。
然后将仓库克隆到本地，将刚刚写的博客所有代码跟文件，统统复制到新的目录`你的用户名.github.io`中 ，这个新的目录以后就是博客项目目录。

![微信图片_20200806181236.png](https://i.loli.net/2020/08/06/BEo7AejJNmsKWI6.png)



然后在项目目录中找到`.gitignore`（没有就新建一个），编写

```
node_modules/

docs/.vuepress/theme

package-lock.json

public/
```



然后新建一个`deploy.sh` 脚本文件

```powershell
npm run build

cd public

git init

git add -A

git commit -m 'deploy'

git push -f https://github.com/feargadh/feargadh.github.io.git master

cd ../

rm -rf public
```

注意：倒数第三行的 `https://github.com/feargadh/feargadh.github.io.git` 改成你自己的仓库地址

然后双击`deploy.sh`运行，博客打包目录就会上传到GitHub仓库中。

![微信图片_20200806191055.png](https://i.loli.net/2020/08/06/z92wGhbZ7DXFtPg.png)

接着浏览器输入 `https://你的用户名.github.io/`  就是你的博客地址了。



然后因为我们上传到GitHub仓库的是博客打包目录，不是项目目录，如果换电脑了是没有备份源代码的。

这时候需要在GitHub仓库新建一个blogcode分支，用于存放源代码。



在项目目录中打开终端 输入

```powershell
git checkout -b blogcode
```

这样就创建了blogcode分支。



然后新建一个`push.sh`脚本文件。

```powershell
git add .

git commit -m 'push'

git push origin blogcode
```

运行`push.sh`，这样就会将博客源代码备份到仓库的blogcode分支中

![微信图片_20200806192153.png](https://i.loli.net/2020/08/06/CY9ZeocQzMkhw74.png)



之后我们每次编写博客，只需要点击`deploy.sh` 脚本，就会自动将更新打包上传，点击`push.sh`上传源代码。