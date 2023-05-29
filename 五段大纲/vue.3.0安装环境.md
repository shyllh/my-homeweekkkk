1，卸载node.js（如果装了2.0的脚手架想换成3.0的需要先卸载重装，如果没有装过任何vue请从第4部开始）

2，C:\Users\18613\AppData\Roaming 目录下删除npm 和npm-cache(如果装了2.0的脚手架,请先删除)

3，安装新版本的node.js

​		参考：https://www.runoob.com/nodejs/nodejs-install-setup.html

​		》.安装nodejs，自带npm环境。地址：https://nodejs.org/en/download/ 下载node.js

​		》.安装淘宝镜像:npm install -g cnpm --registry=https://registry.npm.taobao.org

4，

```
npm install -g @vue/cli
```

5，

```
vue create myobj
```

选择 y 使用淘宝镜像

![image-20210928152344366](assets/image-20210928152344366.png)



![1566367608994](assets/1566367608994.png)

选择手动配置（Manually）

![1566367635682](assets/1566367635682.png)

上下箭头选择空格键为选中，选中图中几个

![1566367686738](assets/1566367686738.png)

不选history模式

![1566367715080](assets/1566367715080.png)

选less

![1566367731887](assets/1566367731887.png)

选则仅保存时候报错

![1566367773804](assets/1566367773804.png)

保存选择语法检查方式，这里我选择保存就检测

![1566367866348](assets/1566367866348.png)

配置放在package.json里面

![1566367897829](assets/1566367897829.png)

是否保存此创建规则，n

![1566368003189](assets/1566368003189.png)

最后cd到目录，然后运行

![1566368051581](assets/1566368051581.png)



运行http://localhost:8080/#/

表示成功



如果安装less有报错，删除掉less 和less-loader目录，然后配置也删掉重新安装less和less-loader

![1566361019330](assets/1566361019330.png)