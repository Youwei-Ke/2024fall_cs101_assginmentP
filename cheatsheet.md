# <center>计算概论CheatSheet
## <center><font face='楷体' size=4>工学院 柯有为

### <font face='仿宋' size=3>
P.S:这段是自己做大作业的时候加的，markdown文档也是做大作业时做的（原本是手写，最近新学markdown怎么用，正好想练下手hh），也算是对自己做cheatsheet的一个反思。
感觉自己准备考试基本就是在做题练手感；对cheatsheet没有给予太多重视（复习时也看了闫老师发的学长做的cheatsheet，觉得很详细，过一遍、做了些上面的题，差不多了）。我觉得很多代码和知识点自己已经足够熟悉了，而且很多时候出了一些低级语法错误编译器都可以显示出来，所以就记了一些可能有用但脑子一时想不起来的内置函数，然后记了几个自己经常出错的代码，还有几点注意事项，比较简陋。
但是最后考试不尽如人意啊。其实考试时这些东西好像都没什么用，我后来觉得cheatsheet里面总结些比较有代表性、自己平时做得有些卡壳的题要更有意义一些。具体的留在后面写课程总结时说吧；讲这些其实是希望老师不要介意我没有好好做cheatsheet（同时求捞~）

---

### <font face='仿宋' size=4>**一、语言方面**

#### <font face='楷体' size=3>1.字符串相关
- title()
  （每个单词）首字母大写
- upper()/lower()
  （每个字母）大写/小写
- str.split('+')
  将字符串str以+为间隔分开（如果没有的话则默认为空格）
  （闫老师讲过，括号里加东西有可能会出问题，但是自己在做有的题时这个确实挺方便，备注一下以便考试时出bug可以往这方面考虑）
- ord()/chr()
  完成字符与ASCII码的转化（感觉基本没用）

#### <font face='楷体' size=3>2.setdefault()
用于字典，括号内包括两个参数，第一个是键，如果键在字典中则返回相应的值，否则返回第二个参数设置的默认值。
e.g.
输入
```python
classmates={'boys':33,'girls':5}
a=classmates.setdefault('boys',0)
b=classmates.setdefault('others',0)
print(f'{a} {b}')
```
输出
```
33 0
```

#### <font face='楷体' size=3>3.float('inf')
float('inf')表示一个无穷大的数（正无穷大）

#### <font face='楷体' size=3>4.bin()
将数字转化为二进制==字符串==，前面带有'0b'前缀，可以切片去除。
e.g.
输入
```python
a=bin(10)[2:]
print(a)
```
输出
```python
1010
```

#### <font face='楷体' size=3>5.保留小数位数
直接举例~计算5除以7，保留5位小数
输入
```python
a=5/7
print(f'{a:.5f}')
```
输出
```python
0.71429
```

#### <font face='楷体' size=3>6.math库
P.S:使用前记得import math
##### (1)平方根
math.sqrt()
##### (2)取整
- math.floor()
  取下整
- math.ceil()
  取上整
##### (3)组合数
math.comb(n,k)
返回一个数，该数为从n个人中挑出k个人的方法数

### <font face='楷体' size=3>7.匿名函数lambda
一般在排序的时候用的比较多；还是直接举例~比如说要将一个由n个二元组组成的列表按元组的第二个元素顺序排序（第二个相同则看第一个）
```python
n=int(input())
tuples=[]
for _ in range(n):
    x,y=map(int,input().split())
    tuples.append((x,y))
tuples.sort(key=lambda x:(x[1],x[0]))
```

### <font face='仿宋' size=4>**二、几个常用的代码**

#### <font face='楷体' size=3>1.手写二分查找
```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid  # 返回⽬标元素的索引
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1  # 如果未找到⽬标元素，返回 -1
```

#### <font face='楷体' size=3>2.冒泡排序
```python
def BubbleSort(arr):
    for i in range(len(arr) - 1):
        for j in range(len(arr) - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
    return arr
```

### <font face='仿宋' size=4>三、**考试注意**

#### <font face='楷书' size=3>
1.假如想不出来时间复杂度低的方法先把能想到的方法试一下 

2.假如考试有想不出来的题先做后面的 

3.一直过不了可以找一找==坑点==（读题时就要仔细） 

4.计算量过大导致TimeLimit时可以试一试==前缀和== 

5.数据过大导致MemoryLimit时可以考虑==减去一个数==、==取模==等方法 

6.与列表以及其索引有关的题目可以考虑==双指针== 

7.能简化成子问题的题目考虑==递归==和==dp==，有时候可以从==状态转移方程==的角度思考问题 

8.什么算法都想不出来，也明显不能brute force的，大概率有==贪心策略== 

9.假如需要删除优先队列里的元素，考虑==懒删除==