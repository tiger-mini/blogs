# tailwindcss 在vue2中的使用

## 安装
vue3的使用可以参考 [官网](https://www.tailwindcss.cn/docs/guides/vue-3-vite) 对于vue2.x 主要是注意版本问题 如官网给出的提示

> Error: PostCSS plugin tailwindcss requires PostCSS 8.

下面已经整理好vue2.x对应的安装版本，执行安装命令即可

```
npm install tailwindcss@npm:@tailwindcss/postcss7-compat @tailwindcss/postcss7-compat postcss@^7 autoprefixer@^9 --save-dev
```
or
```
yarn add tailwindcss@npm:@tailwindcss/postcss7-compat @tailwindcss/postcss7-compat postcss@^7 autoprefixer@^9 -D
```


### 创建 tailwind.config.js 文件

```
# 创建一个空的tainwind css配置文件
npx tailwindcss init
# or
# 你也可以创建一个包含有所有默认配置的文件
npx tailwindcss init -fill
# 两种方法效果一样
```

如果想个性化一些tailwindcss的配置，那么在tailwind.config.js中设置即可

### 创建 postcss.config.js 文件 并做插件的配置

```
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  }
}
```

### 配置loader插件 如在vue-cli对应工程文件vue.config.js
```
 module.exports = {
    css: {
      loaderOptions: {
        postcss: {
          plugins: [require('tailwindcss'), require('autoprefixer')]
        }
      }
    }
  }
```

### 在main.js中引入tailwindcss样式
```
import "tailwindcss/tailwind.css"
```

### UI效果、IDE效果
![UI浏览效果](https://raw.githubusercontent.com/tiger-mini/assets/main/img/tailwindwcss-UI.png)

![IDE开发效果](https://raw.githubusercontent.com/tiger-mini/assets/main/img/tailwindwcss-ide.png)


### 生产环境上去掉未使用的类，简单的一个配置即可

> 为生产而构建时，请确保配置清除 (purge) 选项以删除任何未使用类，这样生成的文件尺寸最小：


看下前后打包文件vender.css的大小
配置前
![vender css 大小](https://raw.githubusercontent.com/tiger-mini/assets/main/img/tailwindwcss-build-asset-raw.png)
配置后
![vender css 大小](https://raw.githubusercontent.com/tiger-mini/assets/main/img/tailwindwcss-build-asset.png)


```
// tailwind.config.js
purge: [
 './src/**/*.html',
 './src/**/*.js',
]
```

查看官网 [生成您的css](tailwindcss.cn/docs/installation#css)


### 引用

[tailwindcss 中文](https://www.tailwindcss.cn/)

[tailwindcss 英文](https://tailwindcss.com/)

[如何评价CSS框架TailwindCSS？](https://www.zhihu.com/question/337939566/answers/updated)

[tailwindcss在Vue中的简单上手](https://godlanbo.com/blogs/25)

[超简单！怎样在Vue2中使用TailWind Css](https://blog.csdn.net/vx_1097122362/article/details/115563641)
