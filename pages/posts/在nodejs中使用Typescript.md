---
title: 在nodejs中使用Typescript
date: 2021-9-25 15:19:33
description:
tag: Typescript
author: 梁典典
---

##### 1.首先新建一个项目
```bash
npm init -yes
```
##### 2.开启Typescript依赖
```bash
npm install typescript --save-dev
```
安装typescript,现在我们可以通过命令行来使用`tsc`命令
##### 3.安装nodejs类型
```bash
npm install @types/node --save-dev
```
##### 4.使用命令创建一个tsconfig.json文件
用idea的右键菜单也可以
```bash
npx tsc --init --rootDir src --outDir build --esModuleInterop --resolveJsonModule --lib es6 --module commonjs --allowJs true --noImplicitAny true
```
去除了无用的注释它的内容像这样的
```json
{
  "compilerOptions": {
    "target": "es5",
    "lib": ["es6"],
    "module": "commonjs",
    "rootDir": "src",
    "resolveJsonModule": true,
    "allowJs": true,
    "outDir": "build",
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true,
    "strict": true,
    "noImplicitAny": true,
    "skipLibCheck": true                                
  }
}

```
`rootDir`: typescript寻找我们编写代码的地方,现在配置为src目录,现在需要在项目录中创建一个`src`文件夹编写ts代码
##### 5.编写ts代码
新建`src/index.ts`文件
```typescript
console.log("hello 梁典典")
```
执行编译命令`npx tsc`,在项目目录中会自动创建`build/index.js`文件,内容如下
```js
"use strict";
console.log("hello 梁典典");
```
##### 6.配置热重载功能
它将监听你的代码自动进行惹更新
```bash
npm install --save-dev ts-node nodemon
```
项目根目录创建`nodemon.json`文件
```json
{
  "watch": ["src"],
  "ext": ".ts,.js",
  "ignore": [],
  "exec": "ts-node ./src/index.ts"
}
```
在`package,json`新增一个脚本命令
```bash
"start:dev": "nodemon"
```
在命令行执行`npm run start:dev`,就可以自动监听文件更改了
##### 7.创建支持清理和编译的生成版本
安装rimraf
```bash
npm install --save-dev rimraf
```
添加脚本
```bash
"build": "rimraf ./build && tsc",
```
##### 8. 创建生产启动脚本
```bash
"start": "npm run build && node build/index.js"
```
现在可以使用typescript编写代码了

















