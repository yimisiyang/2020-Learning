# 使用pyCharm远程调试服务器端代码

## 1.工具

- pyCharm专业版
- 安装着python的Linux服务器（树莓派也可以当作服务器使用）

## 2. 先展示结果

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200708083527.png)

从上图可以看出我的External Libraries 使用的是我的远程树莓派上的python（我这里使用花生壳实现了内网穿透，故这里端口号不是SSH的22，其实映射的是我的树莓派IP：192.168.50.241:22）

## 3. 设置方法

pyCharm点击：File->Settings->Project Interpreter

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200708084243.png)

在弹出对话框中选择SSH Interpreter,右侧host填内网IP（或做完映射的公网IP或域名），端口号若是内网直接填SSH端口号22，若是公网IP或域名则填你做映射的端口号。Username填，登陆树莓派或服务器的账号，接着下一步 输入账号密码即可。

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/278553fc12a4610d9b7ec6638e6fd44.png)



