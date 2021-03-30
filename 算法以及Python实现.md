# 算法以及Python实现

## 1. Collatz 序列

对所有自然数，如果它是奇数，则对它乘3再加1，如果它是偶数，则对它除以2，如此循环，最终都能够得到1。

参考文档（来源维基百科）：[Collatz猜想](https://zh.wikipedia.org/wiki/%E8%80%83%E6%8B%89%E5%85%B9%E7%8C%9C%E6%83%B3)

**python代码实现**

```python
from typing import Tuple,List
def Collaze(a:int) -> Tuple[List[int],int]:
    """
    返回Collaze序列以及它的长度
    >>>Collaze(4)
    ([4,2,1],3)
    """
    if not isinstance(a,int):  # 判断a是不是整型
        raise TypeError("Must be int, not {}".format(type(a)._name_))
    if a < 1:
        raise ValueError(f"Given integer must be greater than 1, not {a}")
    path = [a]
    while a != 1:
        if a % 2 ==0:
            a = a // 2       # 整除，向下取整
        else:
            a = 3 * a + 1
        path += [a]
    return path, len(path)


# 测试Collaze算法

def test_Collaze():
    assert n31(4) == ([4, 2, 1], 3)
    assert n31(11) == ([11, 34, 17, 52, 26, 13, 40, 20, 10, 5, 16, 8, 4, 2, 1], 15)
    assert n31(31) == (
        [
            31,
            94,
            47,
            142,
            71,
            214,
            107,
            322,
            161,
            484,
            242,
            121,
            364,
            182,
            91,
            274,
            137,
            412,
            206,
            103,
            310,
            155,
            466,
            233,
            700,
            350,
            175,
            526,
            263,
            790,
            395,
            1186,
            593,
            1780,
            890,
            445,
            1336,
            668,
            334,
            167,
            502,
            251,
            754,
            377,
            1132,
            566,
            283,
            850,
            425,
            1276,
            638,
            319,
            958,
            479,
            1438,
            719,
            2158,
            1079,
            3238,
            1619,
            4858,
            2429,
            7288,
            3644,
            1822,
            911,
            2734,
            1367,
            4102,
            2051,
            6154,
            3077,
            9232,
            4616,
            2308,
            1154,
            577,
            1732,
            866,
            433,
            1300,
            650,
            325,
            976,
            488,
            244,
            122,
            61,
            184,
            92,
            46,
            23,
            70,
            35,
            106,
            53,
            160,
            80,
            40,
            20,
            10,
            5,
            16,
            8,
            4,
            2,
            1,
        ],
        107,
    )

if _name_ == "_main_":
    num = 4
    path,length = Collaze(num)
    print(f"The Collaze sequence of {num} took {length} steps. \nPath:{path}")
```

## 2. karatsuba 算法

**Karatsuba算法**是一种快速相乘算法，它由Anatolii Alexeevitch Karatsuba于1960年提出并于1962年发表。

Karatsuba的算法主要是用于两个大数的乘法，极大提高了运算效率，相较于普通乘法降低了复杂度，并在其中运用了递归的思想。基本的原理和做法是将位数很多的两个大数**x**，**y**分成位数较少的数，每个数都是原来**x**和**y**位数的一半。这样处理之后，简化为做三次乘法，并附带少量的加法操作和移位操作。

参考文档（维基百科）：[karatsuba算法](https://zh.wikipedia.org/wiki/Karatsuba%E7%AE%97%E6%B3%95)

**python代码实现**

```python
# 采用 Karatsuba算法实现两个数相乘

def karatsuba(num1, num2):
    """
    >>> karatsuba(15463, 23489) == 15463 * 23489
    True
    >>> karatsuba(3, 9) == 3 * 9
    True
    """
    num1Str, num2Str = str(num1), str(num2)
    
    if num1Str[0] == '-': return -karatsuba(-num1,num2)
    if num2Str[0] == '-': return -karatsuba(num1,-num2)
    if num1 < 10 or num2 <10: return num1 * num2 
    
    maxLength = max(len(num1Str), len(num2Str))
    num1Str = ''.join(list('0' * maxLength)[:-len(num1Str)] + list(num1Str))
    num2Str = ''.join(list('0' * maxLength)[:-len(num2Str)] + list(num2Str))
    
    splitPosition = maxLength // 2
    high1, low1 = int(num1Str[:-splitPosition]), int(num1Str[-splitPosition:])
    high2, low2 = int(num2Str[:-splitPosition]), int(num2Str[-splitPosition:])
    
    z0 = karatsuba(low1, low2)
    z2 = karatsuba(high1, high2)
    z1 = karatsuba((low1 + high1), (low2 + high2))
    return z2 * 10 ** (2 * splitPosition) + (z1 - z2 - z0) * 10 ** (splitPosition) + z0


def main():
    print(karatsuba(15463, 23489))

if __name__ == "__main__":
    main()
```

## 3. Fibonacci 查找

[Fibonacci查找算法讲解](https://blog.csdn.net/luochoudan/article/details/51629338)

这里用到了斐波那契数列的一条性质：前一个数除以相邻的后一个数，比值无限接近黄金分割。

这种查找的精髓在于**采用最接近查找长度的斐波那契数值来确定拆分点。**

**作用：** 给定一个列表，给定一个索引值，使用斐波那契查找法给出对应索引值的下标。

```python
"""
@params
arr: input array
val: the value to be searched
output: the index of element in the array or -1 if not found
return 0 if input array is empty
"""

def fibonacci_search(arr, val):
    """
    >>> fibonacci_search([1,6,7,0,0,0], 6)
    1
    >>> fibonacci_search([1,-1, 5, 2, 9], 10)
    -1
    >>> fibonacci_search([], 9)
    0
    """
    fib_N_2 = 0
    fib_N_1 = 1
    fibNext = fib_N_1 + fib_N_2
    length = len(arr)
    if length == 0:
        return 0
    while fibNext < len(arr):
        fib_N_2 = fib_N_1
        fib_N_1 = fibNext
        fibNext = fib_N_1 + fib_N_2
    index = -1
    while fibNext > 1:
        i = min(index + fib_N_2,(length - 1))
        if arr[i] < val:
            fibNext = fib_N_1
            fib_N_1 = fib_N_2
            fib_N_2 = fibNext -fib_N_1
            index = i
        elif arr[i] > val:
            fibNext = fib_N_2
            fib_N_1 = fib_N_1 - fib_N_2
            fib_N_2 = fibNext - fib_N_1
        else:
            return i
    if (fib_N_1 and index < length - 1) and (arr[index + 1] == val):
        return index + 1
    return - 1

if __name__ == "__main__":
    import doctest
    doctest.testmod()
```

**Python 测试框架doctest**

doctest 是Python 自带的一个模块，它的作用主要是用来测试。doctest的编写过程就像你在一个交互式shell中导入了一个被测试模块，然后一条一条执行被测试模块里面的函数一样。有两个地方可以放doctest测试用例，一个位置是模块的最开头，另一个位置是函数声明语句的下一行（就像上面的例子这样）。除此之外的其它地方不能放，放了也不会执行。[doctest官方参考文档](https://docs.python.org/zh-cn/3/library/doctest.html)

## 4. jump 搜索算法

Jump Search 跳跃搜索算法跟二分查找算法类似，它也是针对有序序列的查找，只是它是通过查找比较少的元素找到目标。当然它需要通过固定的跳跃间隔，这样它相比二分查找效率提高了很多。

算法优点：

一、该算法仅适用于有序数组

二、要跳转的最佳大小为O（√n）， 这使得跳跃搜索O（√n）的时间复杂度。

三、跳跃搜索的时间复杂度在线性搜索（（O（n））和二分查找搜索（O（Log n））之间。

四、二分查找算法相比跳跃搜索更好，但是跳跃搜索有以下优点：跳跃搜索仅遍历一次，而二分查找最多需要O(Log n)，考虑要搜索的元素是最小元素或小于 最小的），我们选用Jump Search。

[参考文档](https://blog.csdn.net/jxw167/article/details/72842857)

```python
import math

def jump_search(arr,x):
    n = len(arr)
    step = int(math.floor(math.sqrt(n)))
    prev = 0
    while arr[min(step, n) - 1] < x:
        prev = step
        step += int(math.floor(math.sqrt(n)))    # math.floor() 向下取整，math.sqrt() 平方根函数
        if prev >= n:
            return -1
    while arr[prev] < x:
        prev = prev + 1
        if prev == min(step, n):
            return -1
    if arr[prev] == x:
        return prev
    return -1

if __name__ == "__main__":
    arr = [0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610]
    x = 55
    print(f"Number {x} is at index {jump_search(arr, x)}")
```

## 5. tabu 搜索算法



```python
import copy
import argparse

def generate_neighbours(path):
    
    dict_of_neighbours = {}
    
    with open(path) as f:
        for line in f:
            if line.split()[0] not in dict_of_neighbours:
                _list = list()
                _list.append([line.split()[1],line.split()[2]])
                dict_of_neighbours[line.split()[0]] = _list
            else:
                dict_of_neighbours[line.split()[0]].append(
                [line.split()[1],line.split()[2]]
                )
```















