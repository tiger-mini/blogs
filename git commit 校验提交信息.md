# 规范commit messages


项目开发中多人合作开发时常态，为了便于规范化的看到对应的修改内容，规范提交格式就显得尤为重要。

此过程中需要用到几个工具 [husky](https://www.npmjs.com/package/husky)、[@commitlint/cli](https://www.npmjs.com/package/@commitlint/cli)、[@commitlint/config-conventional](https://www.npmjs.com/package/@commitlint/config-conventional)



### 介绍

- husky 可以用于实现各种 Git Hook。这里主要用到 pre-commit这个 hook，在执行 commit 之前，运行一些自定义操作。

- @commitlint/cli

- @commitlint/config-conventional



> 注意 husky版本 husky自v6以后，安装便不再在.git/hooks/ 目录下生成相应的钩子。所有有可能安装完后，提交代码时不会有检测动作。 本文档我们使用4.2.3版本


### 安装

```
yarn add husky@^4.2.3  @commitlint/cli @commitlint/config-conventional -D
```


### 创建 commitlint.config.js 文件

```
module.exports = {
    extends: ['@commitlint/config-conventional']
};
```

or

```
module.exports = {
    extends: ['@commitlint/config-conventional'],
    rules: {
        'type-enum': [2, 'always', [
            "feat", "fix", "docs", "style", "refactor", "perf", "test", "build", "ci", "chore", "revert"
        ]],
        'subject-full-stop': [0, 'never'],
        'subject-case': [0, 'never']

    }
};
```


### 配置

```
// package.json
{
    ... ,
    "husky": {
       "hooks": {
              "commit-msg": "commitlint -E HUSKY_GIT_PARAMS"
	    }
	},
    ...
}
```


### 提交演示

拦截到错误
![error msg](https://raw.githubusercontent.com/tiger-mini/assets/main/img/commit-msg.png)


按规范提交后正常

![success](https://raw.githubusercontent.com/tiger-mini/assets/main/img/commit-msg-success.png)





### 引用

[git commit校验代码格式](https://blog.csdn.net/wh1t3z/article/details/121630908)

