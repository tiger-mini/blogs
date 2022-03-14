# Pre-commit：如何使用 husky、lint-staged和prettier优化你的项目

代码风格git commit 提交时统一处理。避免风格的不一致性。 其中使用到了三个工具。 [pretter](https://www.npmjs.com/package/prettier)、[husky](https://www.npmjs.com/package/husky)、[lint-staged](https://www.npmjs.com/package/lint-staged)


### 介绍

- prettier 用来优化代码格式，比如缩进、空格、分号等等。
- husky 可以用于实现各种 Git Hook。这里主要用到 pre-commit这个 hook，在执行 commit 之前，运行一些自定义操作。
- lint-staged 用于对 Git 暂存区中的文件执行代码检测。

### 安装

```
yarn add husky lint-staged prettier -D
```
or
```
npm install husky lint-staged prettier --save-dev
```


### 增加 .prettierrc 文件 

```
// .prettierrc
{
  "trailingComma": "es5", // 尾随逗号
  "tabWidth": 4, // 缩进
  "semi": true, // 句尾分号
  "singleQuote": true, // 单引号
  "end-of-line": "lf" // 换行符
}
```

### 配置

```
// package.json
{
  ...,
  "husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
  "lint-staged": {
    "*.{js,vue}": [
      "prettier --write",
      "vue-cli-service lint",
      "git add"
    ]
  },
  ...
}
```



### 生效

这样，当在终端输入 git commit命令提交代码的时，Lint 程序便会自动检查本次提交所修改的文件是否符合本项目的代码规范。如果代码不符合规范，便会拒绝提交代码。

如果想要跳过 Lint 程序，可以使用 git commit -no-verify 进行提交。




### 引用

[Pre-commit：如何使用 husky、lint-staged和prettier优化你的项目](https://blog.csdn.net/flitrue/article/details/106328972)