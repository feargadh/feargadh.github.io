---
title: 在markdown中插入Vue组件
date: 2020-06-22
tags:
 - Vue 
categories:
 - 教程
---

<!-- more -->

根据[官方文档](https://vuepress.vuejs.org/zh/guide/using-vue.html) 描述，所有在 `.vuepress/components` 中找到的 `*.vue` 文件将会自动地被注册为全局的异步组件，如图所示。

![image-20200805210006797.png](https://i.loli.net/2020/08/06/mSbZdYOfkxCo92l.png)

先在 `Ios-toggle.vue`中编写开关组件，然后回到`Card.vue`中，像平时使用Vue组件一样使用。

比如我这里是要将三个Ios开关，插入到`Card.vue`中。



回到MarkDown中，在MarkDown中使用

```md
<ClientOnly>
  <Card></Card>
</ClientOnly>
```

就会如下图一样，在MarkDown中展示`Card组件`。



<ClientOnly>
  <Card></Card>
</ClientOnly>

