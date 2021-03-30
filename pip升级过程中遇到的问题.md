# pip升级过程中遇到的问题

## 问题描述：

windows下安装的python3.6，由于手贱使用了以下命令对pip进行了升级。

```pip
pip install --upgrade pip
```

再次使用pip时就会报以下错误。

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200502161921.png)

## 先说解决方法：

在命令提示符下输入以下命令：

```
python -m ensurepip
```

这样你的pip就救活了。

**pip的正确升级姿势**

```
python -m pip install --upgrade pip
```

## 问题产生原因

windows下有一个pip的exe文件，应该是pip启动器，因为win的exe不能自己删除自己，所以导致出错，因此必须使用 `python -m pip install --upgrade pip`来进行更新，这样启动器就是python而不是pip.exe了。