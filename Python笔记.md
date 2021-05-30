# Python笔记

## 使用help(函数)可以查看具体参数解析

## Python的编码格式

![image-20210304155453726](C:\Users\刘清华\AppData\Roaming\Typora\typora-user-images\image-20210304155453726.png)

## 一切皆对象

**Python中，一切皆对象，都有id、value、type这三个属性，id可以理解为内存地址，value是实际存储的值，type是类型**

id可以通过id()获取

type可以通过type()获取



##可变与不可变对象

在Python中像字符串、整数、元组等都是不可变对象，不可变的含义是：

开辟内存空间后存储的内容不能改变，如果改变则会开辟一块新的内存空间存储内容，也就是说改变后id()也会改变

可变的含义是：内存空间内存储的内容可以改变，改变后的id()不会发生改变，像列表、字典、集合等等都是可变对象



## 对象的布尔值

Python一切皆对象，所有对象都有一个布尔值，获取对象的布尔值使用内置函数bool()

以下对象的布尔值为False：

```python
False
数值0
None
空字符串  ""
空列表   []  或者  list()
空元组   ()  或者  tuple()
空字典   {}  或者  dict()
空集合   set()
```



## == 与 is

**==比较的是value是否相同，is比较的是id是否相同**

```python
[11,22] == [11,22]    #比较内容，结果为True
[11,22] is [11,22]    #比较id，结果为False
```



## 条件语句

```python
# if else单分支结构
if xxx:
  执行语句1
else xxx:
  执行语句2
  
# if elif else 多分支结构
if xxx:
  执行语句1
elif xxx:
  执行语句2
elif xxx:
  执行语句3
else:
  执行语句4
```



## 条件表达式

条件表达式是if...else语句的简写，用于条件赋值，类似于其他语言中的三元表达式:

a = x if 判断条件 else y  

当判断条件为True时a的值为x，当判断条件为False时a的值为y

Python语言中没有三元表达式，所以采用条件表达式作为代替

```python
a = 100 if 3 > 1 else 0    # a = 100
b = 1 if 1 > 3 else 0    # a = 0
```



## 内置range函数

### 作用

生成个整数序列，返回值是一个迭代器对象

### 语法

可以接收一个、两个、三个参数

当接收一个参数a时，生成[0,a)步长为1的整数序列

当接收两个参数a，b时，生成[a,b)步长为1的整数序列

当接收三个参数a,b,c时，生成[a,b)步长为c的整数序列

```python
# 一个参数
l = range(5)   # 需要使用list(l)查看，结果为[0,1,2,3,4]
# 两个参数
l = range(1, 5)   # 需要使用list(l)查看，结果为[1,2,3,4]
# 三个参数
l = range(1, 5, 3)   # 需要使用list(l)查看，结果为[1, 4]
```

###  优点

不管range表示的整数序列有多长，所有的range对象占用的内存空间都是相同的，因为仅仅需要存储start、stop、step，只有当用到range对象时，才会计算序列的长度

in和not in判断整数序列中是否存在指定的整数

### 作用

通常用于循环语句中，python中没有常规的for(int i = 0;....)这种循环，只有for-in循环，所以常用for i in range(n)来代替for(i)循环



## 循环结构

### while循环

while 条件表达式:

   执行语句

```python
a = 10
b = 0
while(a > 0):
  b ++
  a --
print(b)
```

### for-in循环

注意：for-in遍历的对象必须是可迭代对象，可迭代对象有：字符串、列表...

语法结构：

for 自定义变量 in 可迭代对象：

​    自定义变量相关的操作  

```python
for item in "Python":
  print(item)
```

### 流程控制

#### break

与其他语言一样，退出当前这层循环

#### continue

与其他语言一样，退出当前这一次循环进入下一次循环



### 循环中的else语句

与其他语言不同，Python的循环语句后面可以加一个else语句，当循环没有遇到break，正常执行循环结束之后就会进入else语句中；如果是遇到break而结束循环就不会进入else语句中

```python
for i in range(3):
  pwd = input("请输入密码：")
  if pwd == '888':
    print("密码正确")
    break
  else:
    print("密码错误，请再次输入")
else:
  print("密码错误的次数超过三次")
```



## 列表

Python中的列表相当于其他语言中的数组

### 列表的创建

直接创建：list1 = [1,"x"]

使用内置的list函数创建：list2 = list([1,"x"])

使用列表生成式创建：list3 = [i for i in range(1,3) ]

### 获取列表中对应元素的下标

使用.index(元素)即可获取该元素在列表中的下标

如果列表中包含多个相同的元素，则返回第一个位置

如果列表中没有该元素则会报错

**还可以在指定的下标中查找，起始结束位置作为第二三个参数，注意结束位置不包括**

```python
list1 = ["hello","world",1,"hello"]
list1.index("hello")  # 结果是0
list1.index("hello", 1, 3)  # 查找不到，报错,查找范围是[1,3)
```

### 列表的裁剪/切片

Python中的列表裁剪会返回一个新的列表，原来的列表不会改变。

语法与获取单个元素类似：列表名[起始位置: 结束位置: 步长]

注意不包含结束位置的元素

如果步长为负数，则从将第一个参数作为起始位置，第二个参数作为结束位置反着将列表截取

```python
list1 = [1,2,3,4,5,6,7]
list2 = list1[1:6:1]  #结果是：[2, 3, 4, 5, 6]
list3 = list1[1:6:2]  #结果是：[2, 4, 6]
list4 = list1[6:1:-1]  #结果是：[7, 6, 5, 4, 3]
```

### 列表的遍历

使用for-in循环可以遍历列表

### 列表元素的添加

#### 在列表末尾添加一个元素

列表名.append(添加的元素)

```Python
list = [10,20,30]
list.append(40)  # list = [10,20,30,40]
```

#### 在列表末尾添加至少一个元素

列表名.extend(添加的内容) 

```python
list = [10,20,30]
list2 = [50,60]
list.extend(list2)  # list = [10,20,30,50,60]
```

#### 在列表任意位置添加一个元素

列表名.insert(插入的位置，添加的内容)

```python
list = [10,20,30]
list.insert(1,99)  # list = [10,99,20,30]
```

### 列表元素的删除

#### 删除指定元素

列表名.remove(删除的元素)

如果元素不存在则会报错，如果存在多个则只会删除第一个

```python
list = [10,20,30]
list.remove(10)  # list = [20,30]
```

#### 删除指定位置的元素

列表名.pop(删除元素的索引值)

如果参数为空，则默认删除最后一个元素

```python
list = [10,20,30]
list.remove(1)  # list = [10,30]
```

#### 清除列表

列表名.clear()

```python
list = [10,20,30]
list.clear()  # list = []
```

#### 删除列表对象

```python
list = [10,20,30]
list.del()  # list不存在
```



### 列表元素的修改

可以使用切片赋值的操作，对切片进行重新赋值，这样就修改了列表：

```python
list = [10,20,30,40,50,60]
list[1,3] = [5,6,7]  # list = [10,5,6,7,40,50,60]
```



### 列表的排序

**有两种方式，一种在原来的列表上进行排序，另一种会产生一个新的列表**

#### 在原列表上排序

列表名.sort()

如果要倒序，则列表名.sort(reverse=True)

```python
list = [5,6,3,1,4,2]
list.sort()  # list = [1,2,3,4,5,6]
list.sort(reverse=True)  # list = [6,5,4,3,2,1]
```



#### 生成新的排序列表

列表名.sorted()

如果要倒序，则列表名.sorted(reverse=True)

```python
list = [5,6,3,1,4,2]
list2 = list.sorted()  # list2 = [1,2,3,4,5,6]
list2 = list.sorted(reverse=True)  # list2 = [6,5,4,3,2,1]
```



### 列表生成式

利用range函数生成列表：

```python
list = [i for i in range(1,10)]
```



## 字典

 ### 字典的创建

+ 直接创建：dict = {"name":"张三", "age":10}

+ 使用dict函数创建：dict1 = dict(name="张三",age=10)

+ 使用字典生成式创建：

  ```python
  items = ['Fruits', 'Books', 'Others']
  prices = [96, 87, 83]
  
  dict = {item: price for item, price in zip(items, prices )}
  #dict = {'Fruits': 96, 'Books': 87, 'Others': 83}
  ```

  

**注意：直接创建时key值如果是字符串需要加引号，而使用dict函数创建则不需要加引号**



### 获取字典中的元素

有两种方式可以获取字典中的value，一种是[key]的方式，另一种是get()方式:

其中get方式还可以传入第二个参数，表示获取不存在的value返回的值

```python
dict = {"name":"张三", "age":10}
# [key]方式获取字典的value
print(dict["name"])
# get()方式获取字典的value
print(dict.get("name"))
print(dict.get("wife","zz"))  # 得到的是“zz”
```

**二者的区别是：[key]的方式获取不存在的value会报错，而get()方式获取不存在的value会返回None**



### 判断字典中是否含有某key

使用in 判断：

"name" in dict/ "name" not in dict

会返回true或者false



### 删除字典中的key

del dict[key]

如果需要清空字典，则使用dict.clear()

```python
dict = {"name":"张三", "age":10}
del dict["name"]  #dict = {"age":10}
dict.clear()   # dict = {}
```



### 新增/修改字典

```python
dict["name"] = "李四"
```



### 获取字典视图

+ 获取字典中所有key：keys()，可以通过list()转成列表
+ 获取字典中所有value：values()，可以通过list()转成列表
+ 获取字典中所有的key，value键值对：items()，可以通过list()转成列表，列表内的键值对是一个元组



### 字典元素的遍历

**for item in dict:**

item就是字典中的key



### 字典生成式

如果我们需要将两个列表中的元素组合成为一个字典，也就是说一个列表中的元素作为key，另一个列表中的元素作为value，可以使用字典生成式

字典生成式的基本格式：

```python
items = ['Fruits', 'Books', 'Others']
prices = [96, 87, 83]

dict = {item: price for item, price in zip(items, prices )}
#dict = {'Fruits': 96, 'Books': 87, 'Others': 83}
```



## 元组

### 元组的创建

有两种方式：

+ 直接创建：tup = ('Python',3,4) 或者省略小括号：tup = 'Python',3,4
+ + 如果直接创建的元组只有一个元素后面需要加一个逗号tup = (1, )
+ 使用dict函数创建：tup1 = tuple(('Python',3,4))



### 元组的特点

**元组存储的是对象的引用，本身是不可变对象。就是说不能修改元组中对象的地址，比如整数型是不允许被修改的；但是像列表这种可变对象，在修改时地址不会改变，是可以被修改的**



### 元组的遍历

同样是采用for in 循环：

```python
tup = (1, 5, 6, 7)
for item in tup:
    print(item)
    # 1 5 6 7 
```



## 集合

### 集合的创建

**注意：集合中的元素不能重复**

+ 直接创建：s = {1,2,3,4,5,6}

+ 使用内置函数set()创建：可以将列表、range、元组、字符串转换成集合
+ + s = set([1,2,3]) 
  + s = set(range(1, 3))
  + s = set('Python')



### 集合的相关操作

#### 判断集合中是否含有某一元素

使用in或者not in判断集合中是否含有某一元素：

```python
s = {1,2,3,4,5}
print(10 not in s)    # True
print(10 in s)       #False
```

#### 集合元素的添加

添加一个元素：集合名.add()

```python
set = {10,20,30}
list.add(40)  # set = {10,20,30,40}
```

添加多个元素：集合名.update()

```python
set = {10,20,30}
list.update({40,50})  # set = {10,20,30,40,50}
list.update((40,50))  # set = {10,20,30,40,50}
list.update([40,50])  # set = {10,20,30,40,50}         
```

#### 集合元素的删除

删除一个元素，如果不存在则会报错：集合名.remove()

```python
set = {10,20,30}
list.remove(30)  # set = {10,20}
list.remove(50)  # 报错
```

删除一个元素，如果不存在不会报错：集合名.discard()

```python
set = {10,20,30}
list.discard(30)  # set = {10,20}
list.discard(50)  # 不报错
```

删除一个任意元素：集合名.pop()

```python
set = {10,20,30}
list.pop()  # set = {10,20}
```

清空集合：集合名.clear()

```python
set = {10,20,30}
list.clear()  # set = {}
```



### 集合的关系

#### 判断集合是否相等

可以通过==或者!=:

```python
s = {10,20,30,40}
s2 = {30,40,20,10}
s == s2  #True
s != s2  #False
```

#### 判断集合是否是另一个的子集

使用issubset

```python
s1 = {10,20,30,40,50,60}
s2 = {10,20,30,40}
s3 = {10,20,90}
s2.issubset(s1)  #True
s3.issubset(s1)  #False
```

#### 判断集合是否是另一个的超集

使用issuperset

```python
s1 = {10,20,30,40,50,60}
s2 = {10,20,30,40}
s3 = {10,20,90}
s1.issuperset(s2)  #True
s3.issuperset(s3)  #False
```

#### 判断集合是否有交集

使用isdisjoint

**注意：没有交集为True，有交集为False**

```python
s1 = {10,20,30,40}
s2 = {10,20,40}
s3 = {90}
s1.isdisjoint(s2)   #False
s1.isdisjoint(s3)   #True
```



### 集合的数据操作

#### 求集合的交集

使用intersection或者&：

```python
s1 = {10,20,30,40}
s2 = {10,20,40}
print(s1.intersection(s2))  #{10,20,40}
print(s1 & (s2))     #{10,20,40}
```

#### 求集合的并操作

使用union或者|：

```python
s1 = {10,20,30}
s2 = {10,20,40}
print(s1.union(s2))  #{10,20,30,40}
print(s1 | (s2))     #{10,20,30,40}
```

#### 求集合的差操作

使用difference或者-：

```python
s1 = {10,20,30}
s2 = {10,20,40}
print(s2.difference(s1))   #{40}
print(s2 - s1)  #{40}
```

#### 求集合的对称差值操作

对称差值就是去掉两个集合中的重复元素剩下的元素

使用symmetric_difference或者^

```python
s1 = {10,20,30}
s2 = {10,20,40,50}
print(s2.symmetric_difference(s1))   #{30,40,50}
print(s2 ^ s1)  #{30,40,50}
```



### 集合生成式

就是将列表生成式的[]换成{}即可

```python
list = {i for i in range(1,10)}
```



##字符串

**与元组一样，字符串也是一种不可变的数据类型**

### 字符串的驻留机制

Python中相同的字符串只保留一份拷贝，后续创建相同的字符串时，不会开辟新的空间，而是把该字符串的地址赋给新创建的变量

```python
a = 'python'
b = "python"
print(id(a) == id(b))   # True
```



### 字符串的查询操作

+ 查找子串第一次出现的位置，不存在抛出异常：
+ + index()
+ 查找子串最后一次出现的位置，不存在抛出异常：
+ + rindex()
+ 查找子串第一次出现的位置，不存在返回-1：
+ + find()
+ 查找子串最后一次出现的位置，不存在返回-1：
+ + rfind()



### 字符串的大小写转换

转换后会产生一个新的字符串

+ 把字符串中所有的字符都转成大写字母：
+ + upper()
+ 把字符串中所有的字符都转成小写字母：
+ + lower()
+ 把字符串中所有大写字母转成小写字母，所有小写字母转成大写字母：
+ + swapcase()
+ 把第一个字符转换为大写，其余字符转换为小写：
+ + capitalize()
+ 把每一个单词的第一个字符转换为大写，每个单词的剩余字符转换为小写：
+ + title()



### 字符串内容对齐

+ 居中对齐，第1个参数指定宽度，第2个参数指定填充符(可选,默认空格),若设置的宽度小于实际宽度则返回原字符串
+ + center()
+ 左对齐，第1个参数指定宽度，第2个参数指定填充符(可选,默认空格),若设置的宽度小于实际宽度则返回原字符串
+ + ljust()
+ 右对齐，第1个参数指定宽度，第2个参数指定填充符(可选,默认空格),若设置的宽度小于实际宽度则返回原字符串
+ + rjust()
+ 右对齐，左边用0填充，只接受一个参数，用于指定字符串的宽度，若设置的宽度小于实际宽度则返回原字符串
+ + zfill()



### 字符串的分割

+ split()

+ + 从字符串的左边开始分割，默认的分隔标识是空格，返回值是列表

  + 可以通过参数sep来指定分割标识

  + 可以通过参数maxsplit指定最大分割次数，在经过最大分割次数后，剩余部分将单独作为一部分

  + ```python
    str = 'hello python'
    print(str.split())  # ['hello', 'python']
    print(str.split(sep='o'))   # ['hell', ' pyth', 'n']
    print(str.split(sep='o', maxsplit=1)) # ['hell', ' python']
    ```

    

+ rsplit()

+ + 从字符串的右边开始分割，默认的分隔标识是空格，返回值是列表

  + 可以通过参数sep来指定分割标识

  + 可以通过参数maxsplit指定最大分割次数，在经过最大分割次数后，剩余部分将单独作为一部分

  + ```python
    str = 'hello python'
    print(str.split())  # ['hello', 'python']
    print(str.split(sep='o'))   # ['hell', ' pyth', 'n']
    print(str.split(sep='o', maxsplit=1)) # ['hello pyth', 'n']
    ```




### 判断字符串

+ 判断字符串是不是合法的标识符(合法标识符：字母数字下划线)
+ + isidentifier()
+ 判断字符串是不是全部由空白字符组成
+ + isspace()
+ 判断字符串是不是全部由字母组成
+ + isalpha()
+ 判断字符串是不是全部由十进制的数字组成
+ + isdecimal()
+ 判断字符串是不是全部由数字组成
+ + isnumeric()
+ 判断字符串是不是全部由数字和字母组成
+ + isalnum()



### 字符串的替换与合并

+ 替换字符串中的内容，返回一个新的字符串，第三个参数可以省略，省略则替换全部符合条件的

+ + replace(要被替换的内容，替换后的内容，换几次)

+ 合并多个字符串，将列表或元组中的字符串合并成一个字符串，合并方式是中间加上主元素

+ + join()

  + ```python
    s = '|'.join(['js','css','html'])
    print(s)   # s = 'js|css|html'
    s = ' '.join(['java','js','python'])
    print(s)   # s = 'java js python'
    ```

    

### 字符串的比较

+ 运算符：>,>=,<,<=,==,!=
+ 比较规则：先比较字符串中的第一个字符，如果相等则继续比较下一个字符，直到两个字符串中的字符不相等，比较的结果就是最终的结果
+ 比较原理：比较的是原始值，也就是调用内置函数ord可以得到的值，原始值通过内置函数chr可以得到对应字符



### 字符串的切片

切片操作与列表的一致

语法：字符串[起始位置: 结束位置: 步长]

注意不包含结束位置的元素

如果步长为负数，则从将第一个参数作为起始位置，第二个参数作为结束位置反着将列表截取

```python
list1 = '123456'
list2 = list1[1:6:1]  #结果是：'23456'
list3 = list1[1:6:2]  #结果是：'246'
list4 = list1[6:1:-1]  #结果是：'76543'
```



### 字符串格式化

格式化有三种方式：%占位符，{}占位符，f-string

%占位符：使用%s表示字符串占位，%i或者%d表示整数占位，%f表示浮点数占位。后面使用 % （value1，value2，...）来表示实际显示的内容

{}占位符：使用{index}来表示占位，后面使用.format(value1,value2...)来表示实际显示的内容

f-string：字符串引号前面加上f，使用{变量名}来表示实际内容

```python
name = 'Frank'
age = 18
# % 占位符
str1 = '我叫%s,我今年%i岁了' % (name, age)     #我叫Frank,我今年18岁了
# {} 占位符
str2 = '我叫{0},我今年{1}岁了'.format(name, age)#我叫Frank,我今年18岁了
# f-string
str3 = f'我叫{name},我今年{age}岁了'  #我叫Frank,我今年18岁了
```



### 字符串编码转换

编码：将字符串转换为二进制数据bytes，使用encode

解码：将bytes类型的数据转换成字符串类型，使用decode

```python
name = '我爱学习'
#编码
print(name.encode(encoding='GBK')) # GBK编码中一个中文占两个字节
print(name.encode(encoding='UTF-8')) # UTF-8编码中一个中文占三个字节
#解码
bytes1 = name.encode(encoding='GBK')
print(bytes1.decode(encoding='GBK'))
bytes2 = name.encode(encoding='UTF-8')
print(bytes2.decode(encoding='UTF-8'))
```





## 函数

### 函数的创建

def 函数名(参数)：

​     函数体

```python
def add(a, b):
  return a + b
```

### 函数的参数定义

#### 个数可变的位置参数

在定义函数时，如果不确定参数的个数，可以在参数前面加一个*定义一个个数可变的位置形参，结果是一个元组：

```python
def fun(*args):
  print(args)
  
fun(10) #(10,)
fun(10,20,30)  #(10,20,30)
```



#### 个数可变的关键词形参

在定义函数时，如果不确定关键词实参的个数时，可以在参数前面加两个*定义个数可变的关键字形参，结果是一个字典

```python
def fun(**args):
  print(args)
  
fun(a=10) # {'a':10}
fun(a=10,b=20,c=30)  # {'a':10,'b':20,'c':30}
```



#### 列表和字典作为函数的参数

列表作为函数的参数，也就是作为位置形参，可以在列表前面加一个*来将列表值展开：

```python
def func(a,b,c,d):
  print(a,b,c,d)
  
list = [1,2,3,4]
func(*list)
```

字典作为函数的参数，也就是作为关键字形参，可以在字典前面加两个*来将字典值展开：

```python
def func(a,b,c,d):
  print(a,b,c,d)
  
dict = {'a':1,'b':2,'c':3,'d':4}
func(**dict)
```



## 异常处理

### try-except

在执行try代码中遇到错误就会进入到except代码中执行

try：

​      可能出现异常的代码

except 错误类型1：

​      出现该错误时执行的代码

except 错误类型2：

​      出现该错误时执行的代码

......

```python
try:
  a = int(input('请输入第一个整数'))
  b = int(input('请输入读儿歌整数'))
  resukt = a / b
  print('结果为：',result)
except ZeroDivisionError:
  print('对不起，除数不允许为0')
except ValueError:
  print('只能输入数字')
print('程序结束')
```



### try-except-else

在执行try代码中遇到错误就会进入到except代码中执行，如果没有遇到错误则进入else代码中执行

try：

​      可能出现异常的代码

except 错误类型1：

​      出现该错误时执行的代码

except 错误类型2：

​      出现该错误时执行的代码

else：

​      如果不出现错误执行的代码



### try-except-else-finally

在执行try代码中遇到错误就会进入到except代码中执行，如果没有遇到错误则进入else代码中执行，无论有没有出现错误最终都会进入到finally中执行

try：

​      可能出现异常的代码

except 错误类型1：

​      出现该错误时执行的代码

except 错误类型2：

​      出现该错误时执行的代码

else：

​      如果不出现错误执行的代码

finally:

​      无论有没有错误最终都会执行的代码



### 常见的异常类型

+ ZeroDivisionError：除或取模时除数为0
+ IndexError：序列索引超出
+ KeyError：映射中没有这个键
+ NameError：未声明/未初始化对象
+ SyntaxError：语法错误
+ ValueError：无效参数



## 面向对象

### 类的创建

class 类名:

​     类属性

​     实例方法

​     静态方法staticmethod

​     类方法classmethod

```python
class Student:
    # 类属性
    native_place = 'HIT'

    def __init__(self, name):
        self.name = name

    # 实例方法
    def info(self):
        print('我的name是：', self.name)

    # 类方法
    @classmethod
    def cm(cls):
        print('类方法')

    # 静态方法
    @staticmethod
    def sm():
        print('静态方法')
```



### 对象的创建

实例名 = 类名（）

```python
# 拿上面的Student类举例
stu1 = Student('张三')
```



### 类属性、类方法、静态方法

#### 类属性

类属性就是在类中方法外定义的属性，该类的所有类属性都是共享的

#### 类方法

使用@classmethod修饰的方法，在调用时使用类名访问：

例如：Student.cm()

#### 静态方法

使用@staticmethod修饰的方法，在调用时也是使用类名访问：

例如：Student.sm()



### 动态绑定属性和方法

Python是一门动态语言，可以为对象动态的绑定属性和方法

```python
stu1 = Student('张三')
# 动态绑定属性
stu1.gender = '男'
# 动态绑定方法
def show():
  print('我是动态绑定的方法')
stu1.show = show
```



### 私有属性

在Python中没有专门修饰私有属性的关键字，如果需要让属性不能在类外部被访问，可以在属性前面加上两个"_":

```python
class Student:
  def __init__(self,name,age):
    self.name = name
    self.__age = age  # 这样__age在类的外部就不能被轻易访问到

stu1 = Student('张三',20)
print(stu1.name)
print(stu1.__age) # 报错
```



### 继承

#### 继承的语法

class 子类类名(父类1，父类2...)：

​     类内容

**在定义子类时必须在其构造函数中调用父类的构造函数**：super().\__init__()

如果一个类没有继承任何类，则默认继承object

```python
# 父类
class Person:
  def __init__(self,name,age):
    self.name = name
    self.age = age
    
  def info(self):
    print(f'姓名：{self.name}，年龄：{self.age}')
    
# 子类
class Student(Person):
  def __init__(self,name,age,score):
    super().__init__(name,age)
    self.score = score
```

#### 子类重写方法

子类中可以对父类的某个属性或者方法进行重新编写，子类重写的方法中可以通过super().xxx()调用父类中的方法

```python
# 父类
class Person:
  def __init__(self,name,age):
    self.name = name
    self.age = age
    
  def info(self):
    print(f'姓名：{self.name}，年龄：{self.age}')
    
# 子类
class Student(Person):
  def __init__(self,name,age,score):
    super().__init__(name,age)
    self.score = score
  
  # 重写父类的info方法
  def info(self):
    super().info()
    print(f'成绩：{self.score}')
```



### object类

object类是所有类的父类，因此所有类都具有object类的属性和方法

内置函数dir(对象)可以查看指定对象的所有属性

当我们print(对象)的时候实际上就是在调用对象的\__str__()方法，默认是返回对象的内存地址，所以为了方便我们查看对象，会对该方法进行改写



### 特殊属性

对象中有一些带着下划线的属性，这些属性称为特殊属性

+ \__dict__：对象的属性字典，像上面的Student的对象stu1.\_\_dict\_\_返回的就是{'name':'张三',age:15}
+ \_\_class\_\_:对象的类型，像上面的Student的对象stu1.\_\_class\_\_返回的就是\<class '\__main__.Student'>
+ \_\_bases\_\_:类的父类，上面Student.\_\_bases\_\_返回的就是\<class '\__main__.Person'>



### 特殊方法

+ \_\_len\_\_()：通过重写该方法，可以在调用len(对象)时返回我们想要的值
+ \_\_add\_\_()：通过重写该方法，可以让自定义对象具有+的功能，+默认调用该方法
+ \_\_new\_\_()：用于创建对象
+ \_\_init\_\_()：对创建的对象进行初始化
+ + new和init的执行顺序：先进行new创建对象，然后init初始化对象



## 深拷贝与浅拷贝

### 浅拷贝

Python中的拷贝大多数都是浅拷贝，浅拷贝表现为：拷贝时对象包含的子对象内容不进行拷贝而是指向原来的对象的子对象。更改其中一个对象的子对象，另一个对象也会跟着改变

像常用的=赋值操作就是常见的浅拷贝

### 深拷贝

使用copy模块的deepcopy函数，该函数会递归的拷贝对象中的子对象，原来的对象和拷贝出来的对象的所有子对象都不相同，这就是深拷贝。深拷贝的两个对象不会随着一个的改变而改变。



## 模块化

### 创建模块

新建的.py文件都可以作为模块，模块中可以包含任意的函数以及类、变量

### 导入模块

import 模块名称 [as 别名]    后续使用：模块名称.函数/变量/类

或者

from 模块名称 import 函数/变量/类



### Python中的包

包是一个分层次的目录结构，将一组功能相近的模块组织在一个目录下以避免模块名称冲突。

包与目录的区别：包中会有一个\_\_init\_\_.py文件而目录没有

包的导入：import 包名.模块名



### 常用的内置模块

+ sys：与Python解释器及其环境操作相关的标准库，比如getsizeof获取字节大小
+ time：提供与时间相关的各种函数标准库
+ os：提供了访问操作系统服务功能的标准库
+ calendar：提供与日期相关的各种函数的标准库
+ urllib：用于读取来自网上（服务器）的数据的标准库
+ json：用于使用JSON序列化和反序列化对象
+ re：用于在字符串中执行正则表达式匹配和替换
+ math：提供标准算术运算函数的标准库
+ decimal：用于进行精准控制运算精度、有效数位和四舍五入操作
+ logging：提供了灵活记录事件、错误、警告和调试信息等日志信息的功能



## 高级函数

### lambda函数

lambda函数类似于js中的箭头函数，以lambda开头，冒号相当于箭头，前后将参数和return隔开。冒号之前的是参数，冒号之后的是return语句（可以省略return）

```python
add = lambda x,y: x + y
print(func(1,3)) # 4
```



### map函数

**map函数会返回一个map对象，如果需要list()包裹查看**

类似于js中的map函数，接受两个参数，第一个参数是操作函数，描述如何对列表中每一个元素进行操作，第二个参数是要进行操作的list列表

示例：对列表中每一个元素进行平方操作

```python
list = [1, 2, 3, 4, 5, 6]

def f(x):
  return x ** 2

list(map(f, list))    # [1,4,9,16,25,36]
# 或者
list(map(lambda x: x**2,list)) # [1,4,9,16,25,36]
```



### filter函数

**filter函数会返回一个filter对象，如果需要list()包裹查看**

类似于js中的filter函数，接受两个参数，第一个参数是过滤函数，将会保留结果为True的内容，第二个参数是列表

示例：去除列表中的单数保留双数

```python
def func(x):
    return x % 2 == 0

items = [1, 2, 3, 4, 5, 6]

print(list(filter(func, items))) #[2, 4, 6]
# 或者
print(list(filter(lambda x:x % 2 == 0, items))) #[2, 4, 6]
```



### reduce函数

**reduce函数在python3中需要引入from functolls import reduce**

类似于js中的reduce函数，对列表中的内容进行汇总。接受两个参数，第一个参数是操作函数，描述对数组的汇总操作，第二个参数是要进行操作的列表

示例：对列表中所有元素求和

```python
from functools import reduce

def add(x, y):
    return x + y

list = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
res = reduce(add, list)
# 或者
res = reduce(lambda x,y: x + y,list)
print(res) # res = 55
```



