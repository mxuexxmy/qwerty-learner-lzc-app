懒猫微服开发者文档

[https://developer.lazycat.cloud](https://developer.lazycat.cloud/)



移植应用来源：

[https://github.com/RealKai42/qwerty-learner](https://github.com/RealKai42/qwerty-learner)



镜像来源：

[https://hubgw.docker.com/r/ginuerzh/qwerty-learner](https://hubgw.docker.com/r/ginuerzh/qwerty-learner)



安装 `lzc-cli` 懒猫微服开发者工具

```shell
npm install -g @lazycatcloud/lcz-cli@latest --registry=https://registry.npmmirror.com
```



安装 `lzc-dtl` 懒猫微服应用转化工具

```shell
npm install -g lzc-dtl --registry=https://registry.npmmirror.com
```



图标来源：[https://github.com/RealKai42/qwerty-learner/blob/master/public/apple-touch-icon.png](https://github.com/RealKai42/qwerty-learner/blob/master/public/apple-touch-icon.png)



 `lzc-app` 的图标为 `lzc-icon.png`

更改 `apple-touch-icon.png` 为 `lzc-icon.png`

```shell
cp apple-touch-icon.png lzc-icon.png
```



镜像地址

```shell
docker pull hausen1012/qwerty-learner:20241204
```



推送镜像到仓库

```shell
# 推送镜像
lzc-cli appstore copy-image hausen1012/qwerty-learner:20241204
```



编写 `docker-compose.yml`

```shell
version: '3'

services:
  qwertylearner:image:
    image: hausen1012/qwerty-learner:20241204
    ports:
      - '5173:5173'
```



使用 `lzc-dtl`工具转换

```shell
mxuexxmy@DESKTOP-J2NGGP8:~/qwerty-learner-lzc-app$ lzc-dtl

$$\                                   $$\   $$\     $$\
$$ |                                  $$ |  $$ |    $$ |
$$ |$$$$$$$$\  $$$$$$$\          $$$$$$$ |$$$$$$\   $$ |
$$ |\____$$  |$$  _____|$$$$$$\ $$  __$$ |\_$$  _|  $$ |
$$ |  $$$$ _/ $$ /      \______|$$ /  $$ |  $$ |    $$ |
$$ | $$  _/   $$ |              $$ |  $$ |  $$ |$$\ $$ |
$$ |$$$$$$$$\ \$$$$$$$\         \$$$$$$$ |  \$$$$  |$$ |
\__|\________| \_______|         \_______|   \____/ \__|

欢迎使用懒猫微服应用转换器
这个转换器可以把 docker-compose.yml 方便地转换为 懒猫微服 lpk 应用包。

? 请输入应用名称： Qwerty Learner
? 请输入应用包名： cloud.lazycat.app.qwerty-learner
? 请输入应用版本： 0.0.1
? 请选择不支持的平台（默认全平台支持）：
? 是否需要限制系统版本？ No
? 请输入应用描述： 为键盘工作者设计的单词记忆与英语肌肉记忆锻炼软件
? 请输入应用首页：
? 请输入作者： RealKai42
? 请选择应用功能：
? 请输入子域名： qwerty-learner
? 请选择图标文件： lzc-icon.png
? 请选择 docker-compose 文件： docker-compose.yaml
? 请选择路由类型： 从docker-compose读取端口
? 是否添加服务 qwertylearner:image 的端口映射 5173:5173？ Yes
? 请选择 qwertylearner:image:5173 的路由类型： HTTPS路由
? 请输入路由路径（如 /api/）： /
? 请输入目标路径（如 / 或 /api/）： /
? 是否继续添加路由？ No
? [qwertylearner:image] 请选择镜像推送目标： 推送到懒猫微服官方镜像源
[qwertylearner:image] 正在推送镜像到懒猫微服官方镜像源...
命令输出: Waiting ... ( copy hausen1012/qwerty-learner:20241204 to lazycat offical registry)
lazycat-registry: registry.lazycat.cloud/mxuexxmy/hausen1012/qwerty-learner:4ec8dadea887e17e

转换完成！已生成应用包：cloud.lazycat.app.qwerty-learner.lpk
```



安装测试测试

```shell
lzc-cli app install cloud.lazycat.app.qwerty-learner.lpk
```

上架流程

```shell
lzc-cli appstore publish cloud.lazycat.app.qwerty-learner.lpk
```

```shell
mxuexxmy@DESKTOP-J2NGGP8:~/qwerty-learner-lzc-app$ lzc-cli appstore publish cloud.lazycat.app.qwerty-learner.lpk
? 检测到您当前的应用，还没有在懒猫微服中创建，是否使用当前的安装包中的信息进行创建？ [y/n] y
? 请输入应用名称: Qwerty Learner
? 请输入应用ID: cloud.lazycat.app.qwerty-learner
? 请输入应用描述: 为键盘工作者设计的单词记忆与英语肌肉记忆锻炼软件
? 请输入应用简介(简单的概述): 为键盘工作者设计的单词记忆与英语肌肉记忆锻炼软件
? 请选择应用分类: 阅读学习
? 请输入关键词(用逗号分隔): qwerty-learner,单词记忆,背诵单词
? 请输入应用来源: https://github.com/RealKai42/qwerty-learner
? 请输入作者名称: RealKai42
创建 cloud.lazycat.app.qwerty-learner 应用成功!
? 填写 changelog 内容
正在提交审核...
应用提交成功! 请等待审核结果
```



