# 使用 eslint 自动调整 import 代码顺序

在vue或react项目，最常见的操作就是import 样式/组件 到页面或组件中，那么随着迭代，这个页面上的import可以能会加越多。顺序也可能杂乱无章。

为了让每次引入的的内容 自动排好序，不仅仅是处女座的情节，更多的是让编码统一风格。

eslint的 [官网](https://eslint.org/docs/rules/sort-imports#rule-details) 上有下面描述，对于多行导入的不支持重排。

> The --fix option on the command line automatically fixes some problems reported by this rule: multiple members on a single line are automatically sorted (e.g. import { b, a } from 'foo.js' is corrected to import { a, b } from 'foo.js'), but multiple lines are not reordered.

刚好市面上有一款能满足要求的插件 [eslint-plugin-simple-import-sort](https://www.npmjs.com/package/eslint-plugin-simple-import-sort) 。下面进入主题进行介绍


### 安装

```
npm install eslint-plugin-simple-import-sort --save-dev
```

or

```
yarn add eslint-plugin-simple-import-sort -D
```


### 配置插件和规则

// .eslintrc.js 

```
{
    ...,
	plugins: ["simple-import-sort"],
	...,
	rules： {
		...
		"simple-import-sort/imports": "error",
        "simple-import-sort/exports": "error",
		...
	}
}
```

### 添加执行命令

// package.json
{
	...,

    scripts: {
    	...,
    	"lint-fix": "eslint --fix src/**",
    	...,
    }
	...,
}

