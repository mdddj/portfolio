---
title: Flutter 处理图片没有缓存成功的操作
date: 2021年9月25日14:41:56
description: 
tag: Flutter
author: 梁典典
---


# 情景再现
当产品列表页面进入产品详情页面，再返回上一页，部分图片会重新加载，但有的图片不会，有可能是图片太大了需要重新渲染

# 解决办法
再app的main函数中添加

 ```
 void main(){
 	PaintingBinding.instance?.imageCache?.maximumSizeBytes = 1000 << 20;
 }
 ```
问题解决