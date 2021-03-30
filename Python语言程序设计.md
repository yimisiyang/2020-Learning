

# Python语言程序设计

## 一、Python快速入门

### 1.Python 基本语法元素

根据半径计算圆的面积

```python
r = 25
PI = 3.1415926
area = PI * r * r
print("{:.2f}.format(area)")
```

温度转换实例

```python
# TempConvert.py
TempStr = input("请输入带符号的温度值")
if TempStr[-1] in ['f','F']:
    C = (eval(TempStr[0:-1]) - 32) / 1.8
    print("转换后的温度为{:.2f}C".format(C))
elif TempStr[-1] in ['c','C']:
    F = 1.8*eval(TempStr[0:-1]) + 32
    print("转换后的温度为{:.2f}F".format(F))
else:
    print("输入格式错误")
```



### 2.Python基本图形绘制

绘制多个同切圆

```python
import turtle
turtle.pensize(2)
turtle.circle(10)
turtle.circle(40)
turtle.circle(80)
turtle.circle(160)
```

绘制五角星

```python
from turtle import *
color('red','red')
begin_fill()
for i in range(5):
	fd(200)
	rt(144)
end_fill()
```

#### 1.turtle库的基本介绍

- turtle原理

  有一只海龟，其实在窗体正中心，在画布上游走走过的轨迹形成了绘制的图形海龟由程序控制，可以变换颜色、改变宽度等

#### 2.turtle绘图窗体布局

`turtle.setup(width,height,startx,starty)`

setup()设置窗体大小及位置，后两个参数可选

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200522142744.png)

#### 3.turtle空间坐标体系

绝对坐标/相对坐标

```python
turtle.goto(x,y)   #从坐标原点到某一个坐标点
turtle.fd(d)      # 向海龟的正前方向运行
turtle.bk(d)      # 向海龟的反方向运行
turtle.circle(r,angle) #左侧某一点为圆心，曲线运行
```

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200522143535.png)

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200522142858.png)

#### 4.turtle 角度坐标体系

```python
turtle.seth(angle) # -seth()   # 改变海龟行进方向，以角度方式描述。
turtle.left(angel) #  以左的方式改变海龟的运行方向
turtle.right(angle) #以右的方式改变海龟的运行方向
```

#### 5.RGB色彩体系

turtle默认采用小数值来改变颜色，可以切换为整数值

```
turtle.colormode(mode)
```

1.0: RGB小数值模式

255：RGB整数值模式

#### 5.turtle画笔控制函数

```python 
penup()   #将画笔抬起来，海龟在飞行   别名：turtle.pu()
pendown() # 落下画笔，海龟在爬行  别名：turtle.pd()
pensize(width) # 设置画笔的宽度，一次设置一直有效，直到下次重新设置 别名：turtle。width(width)
pencolor(color) # color为颜色字符串 或rgb值
```

颜色举例：

```python
turtle.pencolor("purple")  #字符串
turtle.pencolor(0.63,0.13,0.94) # 小数值
turtle.pencolor((0.63,0.13,0.94)) #元组值
```

#### 6.运动控制函数(走直线&走曲线)

```python
turtle.forward(d)  # 向前行进，走直线，d为行进距离，单位像素，负数代表倒着走。 别名 turtle.fd(d)  
turtle.circle(r,extend=None) #根据半径r绘制extend角度的弧形，默认圆心在海龟左侧r距离的位置,负数为右侧
```

#### 7.方向控制函数

控制海龟面对方向：绝对角度&海龟角度

```python
turtle.setheading(angel)  # 改变行进方向 ，海龟并不行动。 别名： turtle.seth(angle)
```

## 二、Python基础语法

### 1.基本数据类型

整数：可正可负，没有取值范围限制，`pow(x,y)`:计算x的y次方.

整数可用十进制，二进制，八进制，十六进制。

复数类型：

```
pow(2,100)
```

浮点数：与数学上的一致，精度在常规计算中可以忽略。浮点数间运算存在不确定尾数，不是bug

字符串中常用的函数：

```python
len(x)
str(x)
hex(x) #转换为16进制
oct(x) #转换为8进制
chr(u) # u为Unicode编码，返回对应的字符
ord(x) # x 为字符，返回对应的Unicode编码
```

字符串处理方法

```python
str.lower()
str.upper()
str.split(sep = None) #分割字符串
str.count(sub)
str.replace(old,new)
str.center(width[,fillchar]) # fillchar填充的字符，可选参数
str.strip(chars) # 去除str中的指定字符
str.join(iter)  # 在iter 变量除去最后元素外每个元素后增加一个str
```

字符串类型的格式化：

大括号代表一个槽：

```python
"{}爱{}".format("我"，"你")
```

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200522170030.png)

**模块2：time库的使用**

time库包含三类函数

- 时间获取：time() ctime() gmtime()

  - time(): 获取当前时间戳，即计算机内部的时间值，从1970年1月1日0点0分0秒开始计时。
  - ctime(): 获取当前时间并以易读的方式表示，返回字符串。
  - gmtime(): 获取当前时间，表示计算机可处理的时间格式。

- 时间格式化：strftime() strptime()

  - 将时间一合理的方式展现出来

    - 格式化：类似字符串的格式化，需要有展示模板。
    - 展示模板由特定的格式化控制符组成。

  - strftime(tpl, ts): tpl是格式化模板字符串，用来定义输出结果；ts是计算机内部时间类型变量。

    ```python
    import time
    t = time.gmtime()
    time.strftime("%Y-%m-%d %H:%M:%S",t)
    ```

  - strptime():将一段字符串转换为时间，与strftime互补

    ```python
    import time
    timeStr = '2018-01-26 12:55:20'
    time.strptime(timeStr,"%Y-%m-%d %H:%M:%S")
    ```

    

- 程序计时：sleep() perf_conter()

  - 程序计时是指测量起止动作所经历时间的过程。

  - 测量时间：perf_counter()

    返回一个CPU级别的精确时间计数值，单位为秒，由于这个计数值起点不确定，连续调用才有用

  - 产生时间：sleep()

    让程序休眠的时间，单位是秒，可以是浮点数

**文本进度条的实现**

需求分析：

采用字符串方式打印可以动态变化的文本进度条。

进度条需要能在一行中逐渐变化。

```python
#TextProBarV1.py
import time
scale = 10
print("------执行开始------")
for i in range(scale+1):
	a = '*' * i
	b = '.' * (scale - i)
	c = (i/scale) * 100
	print("{:^3.0f}%[{}->{}]".format(c,a,b))
	time.sleep(0.1)
print("------执行结束-------")
```

单行动态刷新

- 刷新的本质是：用后打印的字符覆盖之前的字符

- 不能换行：print() 需要被控制

- 不能回退：打印后光标退回到之前的位置\r

  ```python
  # TextProBarV1.py
  import time
  for i in range(101):
  	print("\r{:3}%".format(i),end="")  # end参数打印完第一行后并不换行，\r参数打印字符串之前使光标退回到行首 
      time.sleep(1)
  ```

完整的进度条打印：

```python
# TextporBarV3.py
import time
scale = 50
print("执行开始".center(scale//2),"-")
start = time.perf_counter()
for i in range(scale+1):
    a = '*' * i
    b = '.' * (scale - i)
    c = (i/scale)*100
    dur = time.perf_counter() - start
    print("\r{:^3.0f}%[{}->{}]{:.2f}s".format(c,a,b,dur), end="")
    time.sleep(1)
print("\n"+"执行结束".center(scale//2, '-'))
```

### 2.程序的控制结构

**程序的分支结构**

- 单分支结构

  ```python
  if <条件>：
  	<语句块>
  ```

- 二分支结构

  ```
  if <条件>：
  	<语句块1>
  else:
  	<语句块2>
  ```

  ```python
  <表达式1> if <条件> else <表达式2>
  ```

- 多分支结构

  ```python
  if <条件>：
  	<语句块1>
  elif:
  	<语句块2>
  	...
  else:
  	<语句块2>
  ```

  **注意：** python中用 and or not 表示逻辑 与 或 非。
  
- 程序的异常处理

  ```python
  try:
  	<语句块1>
  except:
  	<语句块2>
  ```

  指定异常的名字

  ```python
  try:
  	<语句块1>
  except NameError:
  	<语句块2>
  ```

  **注意：** 标注异常类型后，仅响应该类型的异常，异常类型的名字等同于变量名。所有异常名字实在python中定义好了的。

  异常处理的高级使用：

  ```python
  try:
  	<语句块1>
  except:
  	<语句块2>
  else:
  	<语句块3>
  finally:
  	<语句块4>
  ```

  **注意：** finally对应的语句块4一定执行，else对应的语句块3在不发生异常时执行。

**案例：** 身体质量指数BMI

问题需求：

- 输入： 给定体重和身高值
- 输出：BMI指标分类信息（国内和国外）

```python
#CalBMIV1.py
height, weight = eval(input("请输入身高（米）和体重\(公斤)[逗号隔开]："))
bmi = weight / pow(height, 2)
print("BMI 数值为:{:.2f}".format(bmi))
who, nat = "",""
if bmi < 18.5:
    who, nat = "偏瘦", "偏瘦"
elif 18.5 <= bmi < 24:
    who, nat = "正常", "正常"
elif 24 <= bmi < 25:
    who, nat = "正常", "偏胖"
elif 25 <= bmi < 28:
    who, nat = "偏胖", "偏胖"
elif 28 <= bmi < 30:
    who, nat = "偏胖", "肥胖"
else:
    who, nat = "肥胖", "肥胖"
print("BMI 指标为国际:'{0}', 国内:{0}".format(who,nat))
```



### 3.函数和代码复用

**程序的循环结构**

- 遍历循环

  ```python
  for <循环变量> in <遍历结构>：
  	<语句块>
  ```

  计数循环

  ```python
  for i in range(N)：
  	<语句块>
  ```

  计数循环（N次）

  ```python
  for i in range(M,N,K)：
  	<语句块>
  ```

  字符串遍历循环

  ```python
  for c in s: # 遍历s字符串中的每个字符
  	<语句块>
  ```

  列表遍历循环

  ```python
  for item in ls：# 取出列表ls中的每一个元素
  	<语句块>
  ```

  文件遍历循环

  ```python
  for line in fi: # fi 是一个文件标识符，遍历其每行，产生循环
  	<语句块>
  ```

  

- 无限循环

  ```python
  while <条件>：
  	<语句块>
  ```

- 循环控制保留字

  break： 跳出并结束当前整个循环，执行循环后的语句

  continue: 结束当次循环，继续执行后续的循环

- 循环的扩展（高级循环）

  循环与else

  ```python
  for <循环变量> in <遍历结构>:
  	<语句块1>
  else:
      <语句块2>
  ```

  ```python
  while <条件>:
  	<语句块1>
  else:
      <语句块2>
  ```

  当循环没有被break语句退出时，执行else语句块，else语句块作为**正常**完成循环的奖励

**random库概述**

产生随机数的Python标准库，（计算机中的随机数都是伪随机数，由梅森旋转算法生成伪随机序列）

- 基本随机数函数

  seed(): 初始化给定的随机数种子，默认为当前系统时间。 random.seed(10) 产生种子10对应的序列

  random()：产生一个随机数，与随机种子有关。

- 扩展随机数函数

  randint()：产生一个[a,b]之间的整数

  getrandbits()：产生一个k比特长的随机整数

  uniform()：生成一个[a,b]之间的随机小数

  randrange()：生成一个[m,n]之间以k为步长的随机整数

  choice()：从序列seq中随机选取一个元素

  shuffle(): 将序列seq中元素随机排列，返回打乱后的序列

**圆周率计算**

根据公式计算：

```python
# CalPiV1.py
pi = 0
N = 100
for k in range(N):
    pi += 1/pow(16,k)*(4/(8*k+1) - 2/(8*k+4) - 1/(8*k+5) - 1/(8*k+6))
print("圆周率值为：{}".format(pi))
```

蒙特卡洛法：

```python
#CalPiV2.py
from random import random
from time import perf_counter
DARTS = 1000*1000
hits = 0.0
start = time.pref_counter()
for i in range(1,DARTS+1):
    x, y = random(), random()
    dist = pow(x**2 + y**2, 0.5)
    if dist <= 1.0:
        hist = hist+1
pi = 4* (hits/DARTS)
print("圆周率值为：{}".format(pi))
print("运行时间：{:.5f}s".format(time.pref_counter() - start))
```

**lambda函数**

```python
<函数名> = lambda<参数>:<表达式>
```

例：

```python
f = lambda x, y:x+y
```

七段数码管绘制

```python
import turtle
import time
def drawGap():
    turtle.penup()
    turtle.fd(5)
def drawLine(draw):
    drawGap()
    turtle.pendown() if draw else turtle.penup()
    turtle.fd(40)
    drawGap()
    turtle.right(90)
def drawDight(digit):
    drawLine(True) if digit in [2,3,4,5,6,8,9] else drawLine(False)
    drawLine(True) if digit in [0,1,3,4,5,6,7,8,9] else drawLine(False)
    drawLine(True) if digit in [0,2,3,5,6,8,9] else drawLine(False)
    drawLine(True) if digit in [0,2,6,8] else drawLine(False)
    turtle.left(90)
    drawLine(True) if digit in [0,4,5,6,8,9] else drawLine(False)
    drawLine(True) if digit in [0,2,3,5,6,7,8,9] else drawLine(False)
    drawLine(True) if digit in [0,1,2,3,4,7,6,8] else drawLine(False)
    turtle.left(180)
    turtle.penup()
    turtle.fd(20)
def drawDate(date):
    turtle.pencolor("red")
    for i in date:
        if i == "-":
            turtle.write("年",font=("Arial",36,"normal"))
            turtle.pencolor("green")
            turtle.fd(80)
        elif i == '=':
            turtle.write("月",font=("Arial",36,"normal"))
            turtle.pencolor("blue")
            turtle.fd(80)
        elif i == '+':
            turtle.write("日",font=("Arial",36,"normal"))
        else:
            drawDight(eval(i))
def main():
    turtle.setup(1000,350,200,200)
    turtle.penup()
    turtle.fd(-400)
    turtle.pensize(5)
    drawDate(time.strftime("%Y-%m=%d+",time.gmtime()))
    turtle.hideturtle()
    turtle.done()
main()
```

代码复用与函数递归

递归求n的阶乘

```python
def fact(n):
	if n==0:
        return 1
    else:
        return n*fact(n-1)
```

**PyInstaller库的介绍和使用**

将源代码转换为无需源代码的可执行文件，PyInstaller是一个第三方库。

```
pip install pyinstaller
```

Pyinstaller的简单使用（cmd命令行下执行）

```
pyinstaller -F <文件名.py>
```

常用参数

```
-h 查看帮助
--clean 清理打包过程中的临时文件
-D,--onedir 默认值，生成dist文件夹
-F,--oneFile 在dist文件夹中只生成独立的打包文件
-i <图标文件名.ico> 指定打包程序使用的图标（icon）文件
```

**科赫雪花的绘制**

```python
# KochDrawV1.py
import turtle
def koch(size,n):
    if n == 0:
        turtle.fd(size)
    else:
        for angle in [0,60,-120,60]:
            turtle.left(angle)
            koch(size/3, n-1)
def main():
    turtle.setup(600,600)
    turtle.penup()
    turtle.goto(-200,100)
    turtle.pendown()
    turtle.pensize(2)
    level = 3
    koch(400, level)
    turtle.right(120)
    koch(400, level)
    turtle.right(120)
    koch(400, level)
    turtle.hideturtle()
main()
```



### 4.组合数据类型

**集合类型定义及操作**

集合是多个元素的无序组合，与数学中集合概念一致。集合元素之间无序，每个元素唯一，不存在相同的元素。集合元素不可变。

```
A = {"python", 123, ("python",123)}  #集合A
B = set{"pypy123"} #生成集合,p和y 只有一个
B = set() #集合B  使用set创建空集合
```

集合间操作

S | T（并） S- T （差） S & T （交） S^T (补) （ S <= T或 S<T 或S>=T 或 S>T 返回True或 False ）

增强操作符

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200525194234.png)

集合处理方法

```python
s.add(x)        # 如果x不在集合s中，将x增加到s
s.discard(x)    # 移除s中元素x,如果x不在集合s中，不报错
s.remove(x)     # 移除s中元素x,如果x不在集合s中，产生keyError异常
s.clear()       # 移除s中的所有元素
s.pop()         # 随机返回s中的一个元素，更新s,若s为空产生keyError异常
s.copy()        # 返回集合s的一个副本
len(s)          # 返回集合s的元素个数
x in s          # 判断s中元素x,返回true或者false
x not in s
set(x)          # 将其他类型的变量转换为集合类型
```

集合类型的应用场景

- 包含关系的比较

- 数据去重

  ```python
  ls = ["p","p","y","y",123]
  s = set(ls)
  lt = list(s)
  ```

**序列类型及操作**

序列类型的定义

- 序列是具有先后关系的一组元素，序列是一维元素向量，元素类型可以不同（不建议）
- 序列类型是一个基类类型
  - 序列类型衍生出来字符串类型，元组类型，列表类型
- 序列类型包含正向递增序号，和反向递减序号

序列类型通用操作符

```python
x in s  # 如果x是序列s的元素，返回true,否则返回false
x not in s   # 如果x是序列s的元素，返回false,否则返回true
s + t        # 连接两个序列s和t
s*n 或n*s    # 将序列s 复制n次
s[j]        # 索引，返回s中的第i个元素，i是序列的序号
s[i:j] 或 s[i:j:k]   # 切片，返回序列s中第i到j以k为步长的元素子序列。
```

序列的典型类型**列表**

- 列表是一种序列类型，创建后可以被随意修改

- 使用方括号[ ] 或 list() 创建，元素间用逗号，分割。

- 列表中个元素类型可以不同，无长度限制

  ![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200526083718.png)

- 列表类型操作函数和方法

  ![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200526084324.png)

5个函数和方法

```python
len(s)        # 返回序列s的长度
min(s)		  # 返回序列s的最小元素
max(x)        # 返回序列s的最大元素
s.index(x) 
s.index(x,i,j)  #返回序列s从i开始到j位置中第一次出现元素x的位置。
s.count(x)      # 返回出现x的次数
```

序列的典型类型 **元组**

- 元组是一种序列类型，一旦创建就不能被修改。

- 使用小括号（）或 tuple()创建，元素间用逗号，分隔

- 可以使用或不使用小括号，return返回多个元素时其实返回的是一个元组类型。

  ```python
  creature = "cat", "dog", "tiger", "human"   # 定义了一个元组
  color = (0x001100, "blue",creature)
  
  ```

- 元组继承序列类型的全部通用操作

  元组类型继承了序列类型的所有通用操作。

  元组因为创建后不能修改，因此没有特殊操作。

  ```python
  creature = "cat","dog","tiger","human"
  creature = [::-1] # 并不改变原有元组的值，而是生成新的元组。
  color = (0x001100, "blue",creature)
  color[-1][2]
  ```

序列类型的应用场景

- 元组用于元素不改变的应用场景，更多用于固定搭配场景
- 列表更加灵活，它是最常用的序列类型

基本统计值计算实例

```python
# CalStatisticsV1.py
# 获取用户不定长度的输入


def getNum():
    nums = []
    iNumStr = input("请输入数字（回车退出）:")
    while iNumStr != "":
        nums.append(eval(iNumStr))
        iNumStr = input("请输入数字（回车退出）:")
    return nums


# 求这些数的平均值
def mean(numbers):
    s = 0.0
    for num in numbers:
        s = s + num
    return s / len(numbers)


# 计算方差
def dev(numbers, mean):
    sdev = 0.0
    for num in numbers:
        sdev = sdev + (num - mean) ** 2
    return pow(sdev / (len(numbers) -1), 0.5)


# 求中位数
def median(numbers):
    sorted(numbers)
    size = len(numbers)
    if size % 2 == 0:
        med = (numbers[size // 2 - 1] + numbers[size // 2]) / 2  # // 向下取整的意思
    else:
        med = numbers[size // 2]
    return med


def main():
    n = getNum()
    m = mean(n)
    print("平均数：{},方差：{:.2f},中位数：{}.".format(m, dev(n, m), median(n)))

main()

```

字典类型及操作

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200526095714.png)

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200526095942.png)

字典的应用场景

- 映射的表达

jieba库的使用

- 中文分词第三方库
- jieba分词依靠中文词库
  - 利用一个中文词库，确定汉字之间的关联概率
  - 汉字间概率大的组成词组，形成分词结果
  - 除了分词，用户还可以添加自定义的词组

hamlet英文词频统计实例

```python
# CalhamletV1.py
def getText():
    txt = open("hamlet.txt", "r").read()
    txt = txt.lower()
    for ch in '!"#$%&()*+,-./:;<=>?@[\\]^_‘’{|}~':
        txt = txt.replace(ch, " ")
    return txt
def main():
    hamletTxt = getText()
    words = hamletTxt.split()
    counts = {}
    for word in words:
        counts[word] = counts.get(word,0) + 1
    items = list(counts.items())
    items.sort(key=lambda x:x[1], reverse=True)
    for i in range(10):
        word, count = items[i]
        print("{0:<10}{1:>5}".format(word,count))
main()
```

```python
#CalThreeKingdomsV1.py
import jieba
txt = open("threekingdoms.txt", "r", encoding="utf-8").read()
words = jieba.lcut(txt)
counts = {}
for word in words:
    if len(word) == 1:
        continue
    else:
        counts[word] = counts.get(word, 0) + 1
items = list(counts.items())
items.sort(key=lambda x:x[1], reverse=True)
for i in range(15):
    word,count = items[i]
    print("{:<10}{:>5}".format(word,count))
```



### 5.文件和数据格式化

文件是数据的抽象和集合

- 文件是存储在辅助存储器上的数据序列
- 文件是数据存储的一种形式
- 文件展现形态：文本文件和二进制文件

文本文件VS二进制文件

- 文件文件和二进制文件只是文件的展示方式
- 本质上，所有文件都是二进制形式存储
- 形式上，所有文件采用两种方式展示

文件的打开和关闭

- 文件处理的步骤：打开-操作-关闭

  ![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200526141006.png)

文件的打开

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200526150159.png)

自动轨迹绘制

- 需求：根据脚本来绘制图形
- 不是写代码而是写数据绘制轨迹
- 数据脚本是自动化最重要的第一步

数据接口定义：

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200526151422.png)



```python
# AutoTraceDraw.py
import turtle as t
t.title('自动轨迹绘制')
t.setup(800,600,0,0)
t.pencolor("red")
t.pensize(5)
# 数据读取
datals = []
f = open("data.txt")
for line in f:
    line = line.replace("\n", "")
    # map函数的功能将第一个参数的功能作用于第二个参数的每一个元素。
    datals.append(list(map(eval,line.split(","))))
f.close()
# 自动绘制
for i in range(len(datals)):
    t.pencolor(datals[i][3],datals[i][4],datals[i][5])
    t.fd(datals[i][0])
    if datals[i][1]:
        t.right(datals[i][2])
    else:
        t.left(datals[i][2])
t.hidetutle()

```

**一维数据的格式化与处理**

- 如果数据间有序：使用列表类型

  - 列表类型可以表达一维有序数据
  - for循环可以遍历数据，进而对每个数据进行处理

- 如果数据间无序：使用集合类型

  - 集合类型可以表达一维无序数据
  - for循环可以遍历数据，进而对每个数据进行处理

- 一维数据的存储

  - 使用一个或多个空格分隔进行存储，不换行
    - 缺点：数据中不能存在空格
  - 逗号分割：使用英文半角逗号分隔数据进行存储，不换行
    - 缺点：数据中不能由英文逗号
  - 使用特殊符合分隔

- 一维数据的处理

  - 从空格分隔的文件中读入数据

    ```python
    txt = open(fname).read()
    ls = txt.split()
    f.close()
    ```

  - 从特殊符号分隔的文件中读入数据

    ```
    txt = open(fname).read()
    ls = txt.split("$")
    f.close()
    ```

  - 采用空格分割方式将数据写入文件

    ```python
    ls = ["中国","美国","日本"]
    f = open(fname,'w')
    f.write(' '.join(ls))
    f.close()
    ```

  **二维数据的格式化与处理**

  - 列表类型可以表达二维数据（二维列表）
  - 使用两层for循环遍历每个元素
  - 外层列表中每个元素可以对应一行，也可以对应一列

  **CSV数据存储格式（Comma-Separated Values）**

  - 国际通用的一二维数据存储格式，一般.csv扩展名

  - 每行一个一维数据，采用逗号分隔，无空行

  - 如果某个元素缺失，逗号仍要保留

  - 二维数据的表头可以作为数据存储，也可以另行存储

  - 逗号为英文半角逗号，逗号与数据之间无额外空格

  - 从CSV格式的文件中读入数据

    ```python
    fo = open(fname)
    ls = []
    for line in fo:
    	line = line.replace("\n","")
    	ls.append(line.split(","))
    fo.close()
    ```

  - 将数据写入CSV格式的文件

    ```python
    ls = [[ ],[ ], [ ]]
    f = open(fname,'w')
    for item in ls:
    	f.write(','.join(item) + '\n')
    f.close()
    ```

  - 二维列表的遍历

    ```python
    ls = [[1,2],[3,4],[5,6]]
    for row in ls:
        for column in row:
            print(column)
    ```

  **worldcloud库的使用**

  - wordcloud是优秀的词云展示第三方库

  - wordcloud库把词云当作一个 WordCloud对象

    - wordcloud. Word Cloud0代表一个文本对应的词云
    - 可以根据文本中词语出现的频率等参数绘制词云
    - 绘制词云的形状、尺寸和颜色都可以设定

  - worldcloud库常规方法

    ![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200526165810.png)

  - 绘制词云的步骤

    - 步骤1：配置对象参数
    - 步骤2：加载词云文本
    - 步骤3：输出词云文件

    ```python
    import wordcloud
    c = wordcloud.WordCloud()
    c.generate("wordcloud by Python")
    c.to_file("pywordcloud.png")
    ```

    ![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200526171537.png)

  - wordcloud配置参数对象

    ![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200526171736.png)

    ![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200526171957.png)

    ![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/image-20200526173004530.png)

    ![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/image-20200526173130682.png)

    ```python
    import jieba
    import wordcloud
    txt ="我是一个人"
    w = wordcloud.WordCloud(width=1000,font_path="msyh.ttc",height=700)
    w.generate(" ".join(jieba.lcut(txt)))
    w.to_file("pywcloud.png")
    ```

    ```python
    # WordCloudV3.py
    import jieba
    import wordcloud
    f = open("threekingdoms.txt","r",encoding="utf-8")
    t = f.read()
    ls = jieba.lcut(t)
    txt = " ".join(ls)
    w = wordcloud.WordCloud(font_path="msyh.ttc", width = 1000, height = 700,background_color="write")
    w.generate(txt)
    w.to_file("grwordcloud.png")
    ```
    
    

## 三、Python编程思维

### 1.程序设计方法学

#### 1.体育竞技实例

**自顶向下（设计）**

- 解决复杂问题的有效方法
  - 将一个总问题表达为若干个小问题组成的形式
  - 使用同样方法进一步分解小问题
  - 直至，小问题可以用计算机简单明了的解决

**自底向上（执行）**

- 逐步组建复杂系统的有效测试方法
  - 分单元测试，逐步组装
  - 按照自顶向下相反的路径操作
  - 直至，系统各部分以组装的思路都经过测试和验证

#### 2.Python程序设计思维

计算思维真的很重要！！！！！！

#### 3.Python第三方库安装

Python社区：https://pypi.org/

pip安装方法：

```shell
pip install <第三方库>  #安装第三方库
pip install -U <第三方库>   #更新以安装的第三方库
pip uninstall <第三方库>    # 卸载第三方库
pip download <第三方库>     # 下载但并不安装第三方库
pip show <第三方库>   # 显示第三方库的详细信息
pip search <关键词>  # 根据关键词名称搜索第三方库
pip list            # 列出当前系统已经安装的第三方库
```

**主要方法，适合99%以上的情况。**

集成安装方法

Anaconda https://www.continuum.io 支持近800个第三方库

文件安装方法

#### 4.os库的基本使用

**os库之路径操作**

os.path子库以path为入口，用于操作和处理文件路径

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200527082913.png)

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200527083045.png)

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200527083214.png)

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200527083336.png)

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200527083445.png)

**os库之进程管理：**`os.system(command)`

执行程序或命令command,在windows系统中，返回值为cmd的调用返回信息。

**os库之环境参数**

获取或改变系统环境信息

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200527084022.png)

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200527084112.png)

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200527084212.png)

#### 5.第三方库自动安装脚本

```python
# BatchInstall.py
import os
libs = {"numpy","matplotlib","pillow","sklearn","requests","jieba","beautifulsoup4","wheel","networkx","sympy","pyinstaller","django","flask","werobot","pyqt5","pandas","pyopengl","pypdf2","docopt","pygame"}
try：
	for lib in libs:
        os.system("pip install" + lib)
    print("Successful")
except:
    print("Failed Somehow")
```

### 2.Python计算生态纵览

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200527090532.png)

**从数据处理到人工智能**

数据表示->数据清洗->数据统计->数据可视化->数据挖掘->人工智能

- 数据表示：采用合适方式用程序表达数据

- 数据清洗：数据归一化、数据转换、异常值处理

- 数据统计:数据的概要理解、数量、分布、中位数等

- 数据可视化：直观展示数据内涵的方式

- 数据挖掘：从数据分析获得知识，产生数据外的价值

- 人工智能：数据/语言/图像/视觉等方面深度分析与决策

**python库之数据分析**

- Numpy:表达N维数组的最基础库
  - Python接口使用，C语言实现，计算速度优异
  - python数据分析及科学计算的基础库，支撑 Pandas等
  - 提供直接的矩阵运算、广播函数、线性代数等功能
- Pandas: Python数据分析高层次应用库
  - 提供了简单易用的数据结构和数据分析工具
  - 理解数据类型与索引的关系，操作索引即操作数据
  - Python最主要的数据分析功能库，基于 Numpy开发
- SciPy:数学、科学和工程计算功能库
  - 提供了一批数学算法及工程数据运算功能
  - 类似 Matlab，可用于如傅里叶变换、信号处理等应用
  - Python最主要的科学计算功能库，基于Numpy开发

**python库之数据可视化**

- Matplotlib:高质量的二维数据可视化功能库

  - 提供了超过100种数据可视化展示效果
  - 通过matplotlib.pyplot子库调用各可视化效果
  - Python最主要的数据可视化功能库，基于Numpy开发

- Seaborn:统计类数据可视化功能库

  - 提供了一批高层次的统计类数据可视化展示效果
  - 主要展示数据间分布、分类和线性关系等内容
  - 基于 Matplotlib开发，支持 Numpy和 Pandas

- Mayavi：三维科学数据可视化功能库

  - 提供了一批简单易用的3D科学计算数据可视化展示效果
  - 目前版本是 Mayavi2,三维可视化最主要的第三方库
  - 支持 Numpy、 TVTK、 Traits、 Envisage等第三方库

  **python库之文本处理**

- PyPDF2: 用来处理pdf文件的工具集

  - 提供了一批处理PDF文件的计算功能
  - 支持获取信息、分隔/整合文件、加密解密等
  - 完全 Python语言实现，不需要额外依赖，功能稳定

  ![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200527092845.png)

- NLTK：自然语言文本处理第三方库

  - 提供了一批简单易用的自然语言文本处理功能
  - 支持语言文本分类、标记、语法句法、语义分析等
  - 最优秀的 Python自然语言处理库

- Python-docx：创建或更新Microsoft Word文件的第三方库

  - 提供创建或更新。doc.docx等文件的计算功能
  - 增加并配置段落、图片、表格、文字等，功能全面

**Python库之机器学习**

- Scikit-learn ：机器学习方法工具集
  - 提供一批统一化的机器学习方法功能接口
  - 提供聚类、分类、回归、强化学习等计算功能
  - 机器学习最基本且最优秀的 Python第三方库
- TensorFlow: AlphaGo 背后的机器学习计算框架
  - 谷歌公司推动的开源机器学习框架
  - 将数据流图作为基础，图节点代表运算，边代表张量
  - 应用机器学习方法的一种方式，支撑谷歌人工智能应用
- MXNet:基于神经网络的深度学习计算框架
  - 提供可扩展的神经网络及深度学习计算功能
  - 可用于自动驾驶、机器翻译、语音识别等众多领域
  - Python最重要的深度学习计算框架

霍兰德人格分析案例

```python
# HollandRadarDraw
import numpy as np
import matplotlib.pyplot as plt
import matplotlib
matplotlib.rcParams['font.family']='SimHei'
radar_labels = np.array(['研究型（I）','艺术型（A）','社会型（S）','企业型（E）','常规型（C）','现实型（R）'])
data = np.array([[0.40,0.32,0.35,0.30,0.30,0.88],
                 [0.85,0.35,0.30,0.40,0.40,0.30],
                 [0.43,0.89,0.30,0.28,0.22,0.30],
                 [0.30,0.25,0.48,0.85,0.45,0.40],
                 [0.20,0.38,0.87,0.45,0.32,0.28],
                 [0.34,0.31,0.38,0.40,0.92,0.28]])
data_labels = ('艺术家','实验员','工程师','推销员','社会工作者','记事员')
angles = np.linspace(0,2*np.pi,6,endpoint=False)
data = np.concatenate((data,[data[0]]))
angles = np.concatenate((angles,[angles[0]]))
fig = plt.figure(facecolor='white')
plt.subplot(111, polar=True)
plt.plot(angles,data,'o-',linewidth=1,alpha=0.2)
plt.fill(angles,data,alpha=0.25)
plt.thetagrids(angles*180/np.pi,radar_labels)
plt.figtext(0.52,0.95,'霍兰德人格分析',ha='center',size=20)
legend = plt.legend(data_labels,loc=(0.94,0.80),labelspacing=0.1)
plt.setp(legend.get_texts(),fontsize='large')
plt.grid(True)
plt.savefig('holland_radar.jpg')
plt.show()
```

**Python之网络爬虫**

- Requests：最友好的网络爬虫推荐库
  - 提供了简单易用的类HTTP协议网络爬虫功能
  - 支持连接池、SSL、Cookies、HTTP(S）代理等
  - Python最主要的页面级网络爬虫功能库
- Scrapy：优秀的网络爬虫框架
  - 提供了构建网络爬虫系统的框架功能，功能半成品
  - 支持批量和定时网页爬取、提供数据处理流程等
  - Python最主要且最专业的网络爬虫框架
- pyspider:强大的Web页面爬取系统
  - 提供了完整的网页爬取系统构建功能
  - 支持数据库后端、消息队列、优先级、分布式架构等
  -  Python重要的网络爬虫类第三方库

**Python库之Web信息提取**

- Beautiful Soup: HTML和XML的解析库
  - 提供了解析HTML和XML等Web信息的功能
  - 又名 beautifulsoup4或bs4,可以加載多种解析引擎
  - 常与网络爬虫库搭配使用，如 Scrapy、 requests等
- Re:正则表达式解析和处理功能库
  - 提供了定义和解析正则表达式的一批通用功能
  - 可用于各类场景，包括定点的Web信息提取
  - Python最主要的标准库之一，无需安装
- Python-Goose:提供文章类型Web页面的功能库
  - 提供了对Web页面中文章信息/视频等元数据的提取功能
  - 针对特定类型Web页面，应用覆盖面较广
  - Python最主要的Web信息提取库

**Python库之web网站开发**

- Django:最流行的web应用框架
  - 提供了构建eb系统的基本应用框架
  - MTV模式：模型（ model）、模板（ Template）、视图（ Views）
  -  Python最重要的Web应用框架，略微复杂的应用框架
- Pyramid:规模适中的Web应用框架
  - 提供了简单方便构建Web系统的应用框架
  -  不大不小，规模适中，适合快速构建并适度扩展类应用
  -  Python产品级Web应用框架，起步简单可扩展性好
- Flask：web应用开发微框架
  - 提供了最简单构建eb系统的应用框架
  - 特点是：简单、规模小、快速
  - Django >Pyramid > Flask 

**Python库之网络应用开发**

- WeRoBot:微信公众号开发框架
  - 提供了解析微信服务器消息及反馈消息的功能
  - 建立微信机器人的重要技术手段
- aip:百度AI开放平台接口
  - 提供了访问百度AI服务的 Python功能接口
  -  语音、人脸、OCR、NLP、知识图谱、图像搜索等领域
  -  Python百度A应用的最主要方式
- MyQR:二维码生成第三方库
  - 提供了生成二维码的系列功能
  - 基本二维码、艺术二维码和动态二维码

**Python库之图形用户界面**

- PyQt5: Qt开发框架的Python接口
  - 提供了创建Qt5程序的 Python APL接口
  - Qt是非常成熟的跨平台桌面应用开发系统，完备GUI
  - 推荐的 Python GUI开发第三方库
- wxPython：跨平台GUI开发框架
  - 提供了专用于 Python的跨平台GUI开发框架
  -  理解数据类型与索引的关系，操作索引即操作数据
  - Python最主要的数据分析功能库，基于 Numpy开发
- PyGObject: 使用GTK+开发GUI的功能库
  - 提供了整合GTK+、WebKitGTK+等库的功能
  - GTK+:跨平台的一种用户图形界面GU框架
  - 实例：Anaconda采用该库构建GUI

**Python库之游戏开发**

- PyGame：简单的游戏开发功能库
  - 提供了基于SDL的简单游戏开发功能及实现引擎
  - 理解游戏对外部输入的响应机制及角色构建和交互机制
  - Python游戏入门最主要的第三方库
- Panda3D：开源、跨平台的3D渲染和游戏开发库
  - 一个3D游戏引擎，提供 Python和C++两种接口
  - 支持很多先进特性：法线贴图、光泽贴图、卡通渲染等
  - 由迪士尼和卡尼基梅隆大学共同开发
- cocos2d:构建2D游戏和图形界面交互式应用框架
  - 提供了基于 Opengl的游戏开发图形渲染功能
  - 支持GPU加速，采用树形结构分层管理游戏对象类型
  - 适用于2D专业级游戏开发

**Python库之虚拟现实 **

- VR Zero:在树莓派上开发VR应用的Python库
  - 提供大量与VR开发相关的功能
  - 针对树莓派的VR开发库，支持设备小型化，配置简单化
  - 非常适合初学者实践VR开发及应用
- pyovr:Oculus Rift的Python开发接口
  - 针对 Oculus VR设备的 Python开发库
  - 基于成熟的VR设备，提供全套文档，工业级应用设备
  - Python+虚拟现实领域探索的一种思路
- Vizard： 基于Python的通用VR开发引擎
  - 专业的企业级虚拟现实开发引擎
  - 提供详细的官方文档支持多种主流的VR硬件设备，具有一定通用性

**python库之图形艺术**

- Quads：迭代的艺术
  - 对图片进行四分迭代，形成像素风
  - 可以生成动图或静图图像
  - 简单易用，具有很高展示度
- ascii_art：ASCII艺术库
  - 将普通图片转为ASCⅡ艺术风格
  - 输出可以是纯文本或彩色文本
  - 可采用图片格式输出
- turtle:海龟绘图体系

**玫瑰花绘制**

```python
# RoseDraw.py
import turtle as t
# 定义一个曲线绘制函数
def DegreeCurve(n,r,d=1):
    for i in range(n):
        t.left(d)
        t.circle(r,abs(d))
# 初始位置设定
s = 0.2 # size
t.setup(450*5*s,750*5*s)
t.pencolor("black")
t.fillcolor("red")
t.speed(100)
t.penup()
t.goto(0,900*s)
t.pendown()
# 绘制花朵形状
t.begin_fill()
t.circle(200*s,30)
DegreeCurve(60,50*s)
t.circle(200*s,30)
DegreeCurve(4,100*s)
t.circle(200*s,50)
DegreeCurve(50,50*s)
t.circle(350*s,65)
DegreeCurve(40,70*s)
t.circle(150*s,50)
DegreeCurve(20,50*s,-1)
t.circle(400*s,60)
DegreeCurve(18,50*s)
t.fd(250*s)
t.right(150)
t.circle(-500*s,12)
t.left(140)
t.circle(550*s,110)
t.left(27)
t.circle(650*s,100)
t.left(130)
t.circle(-300*s,20)
t.right(123)
t.circle(220*s,57)
t.end_fill()
# 绘制花枝形状
t.left(120)
t.fd(280*s)
t.left(115)
t.circle(300*s,33)
t.left(180)
t.circle(-300*s,33)
DegreeCurve(70,225*s,-1)
t.circle(350*s,104)
t.left(90)
t.circle(200*s,105)
t.circle(-500*s,63)
t.penup()
t.goto(170*s,-30*s)
t.pendown()
t.left(160)
DegreeCurve(20,2500*s)
DegreeCurve(220,250*s,-1)
# 绘制一个绿色叶子
t.fillcolor('green')
t.penup()
t.goto(670*s,-180*s)
t.pendown()
t.right(140)
t.begin_fill()
t.circle(300*s,120)
t.left(60)
t.circle(300*s,120)
t.end_fill()
t.penup()
t.goto(180*s,-550*s)
t.pendown()
t.right(85)
t.circle(600*s,40)

#绘制另一个绿色叶子
t.penup()
t.goto(-150*s,-1000*s)
t.pendown()
t.begin_fill()
t.rt(120)
t.circle(300*s,115)
t.left(75)
t.circle(300*s,100)
t.end_fill()
t.penup()
t.goto(430*s,-1070*s)
t.pendown()
t.right(30)
t.circle(-600*s,35)
t.done()
```













