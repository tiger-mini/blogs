# webstorm 鼠标右键快速创建文件模板

### 效果

![webstorm menu init](https://raw.githubusercontent.com/tiger-mini/assets/main/img/webstorm%20menu%20quick%20init.gif)


### 分步来实现这一效果

#### 1、 先用命令行创建

> 前提： 本地已经安装了ykj-h5-cli 脚手架。没有安装的需先全局安装。 


上面安装的脚手，附带了能创建模板的命令，为 ykj-h5-folder。 使用方式是 


```
ykj-h5-folder init <folder-name>
```

然后 再对应的文件夹目录下执行该命令。如下效果

![cmd init](https://raw.githubusercontent.com/tiger-mini/assets/main/img/webstorm%20menu%20cmd%20init.gif)


有了以上条件之后，就可以进行webstorm的配置了


#### 2、 再在webstorm上配置



##### 1、Setting > Tool > External Tools

![External Tools](https://raw.githubusercontent.com/tiger-mini/assets/main/img/webstorm%20menu%20quick%20init%20step%201.png)



##### 3、点击 + 图标 进行信息录入

![add External](https://raw.githubusercontent.com/tiger-mini/assets/main/img/webstorm%20menu%20quick%20init%20step%202.png)



> Program: 选择到上面的 通过命令方式创建模板对应的cmd命令

> Arguments: 弹框接收文件夹名称。直接使用webstorm 内置变量 $Prompt$.

> Working directory: 创建文件所在目录。直接使用webstorm内置变量即可。 $FileDir$



以上步骤完成之后就出现了最初的效果。