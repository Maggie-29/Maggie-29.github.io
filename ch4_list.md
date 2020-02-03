# Python 第五次课小记

## 第四次课课后习题讲解

1. Write a Python program to convert a list of multiple integers into **a single integer**.

   Sample list: [11, 33, 50]

   Expected Output: 113350

```
result=[] #result是一个list
spam=[11,33,50]
for i in range(len(spam)):
      result=result+str(spam[i]) 
      print(result)
------------------------------------------------------------------------
----> result=result+str(spam[i]) 
TypeError: can only concatenate list (not "str") to list
#错误提示：str(spam[i])是str，不能直接与result这个list相加
```

```
result='' #result是个str
spam=[11,33,50]
for i in range(len(spam)):
    result=result+str(spam[i])
print(result)
------------------------------------------------------------------------
113355
#错误提示：虽然代码跑通了，输出结果看上去也是对的，但依旧不符合题目要求（result此时的形式是str，并非int）

#修改方法：把最后一步 print(result) 改为 print(int(result))
```

我们也可以把列表中每一个值取出为str 再一个个相加 转int





### 4.1.7 用del语句从列表中删除值

```
spam=['cat','rat', 'bat','elephant']
for i in range(len(spam)):
    del spam[i]
------------------------------------------------------------------------
----> del spam[i]
IndexError: list assignment index out of range
```

delete和for循环最好不要一起使用，因为spam的长度在每次删除之后都会变



## 4.4方法

> list.index( ) 在列表中查找值
>
> list.append( ) 在列表末尾添加参数
>
> list.insert( ) 在列表任意下标处添加参数
>
> list.remove( ) 在列表中删除 一个具体的值  #ps: 如果不知道列表具体的值 知道下标的话就用del语句
>
> list.sort( ) 将列表值按American Standard Code for Information Interchange (ascii码)进行排列
>
> （摘自Al Sweigart的Python编程快速上手--让繁琐工作自动化）



除了第一个方法index( )是查看一个值在列表中的下标之外，其余方法在以 "列表名.方法名 ( )"  的形式被调用后可以直接修改列表 （以append（）为例）

```
spam=['rat','bat','cat']
spam.append('cat')
spam
------------------------------------------------------------------------
['rat', 'bat', 'cat', 'cat']
```

但要注意不能写成 "列表名=列表名.方法名" 

因为这是在把你所使用方法( append( ) )的返回值 赋给之前的列表名，所以当我们再次查看列表名的值的时候 会得到None这个结果（方法的返回值）

```
spam=['rat','bat','cat']
spam=spam.append('cat')
print(spam)
------------------------------------------------------------------------
None
```

  



### 补充sort( )的用法

1. 如果列表中既有str这种数据类型，也有int这种数据类型，Python会无法比较不同的值对他们进行排序
2. list.sort ( ) 将列表值按ascii码进行排列  顺序为：数字、大写字母、小写字母
3. list.sort (reverse=True) 按ascii码逆序排序 顺序为：小写字母、大写字母、数字



### 随堂小练习

#用户输入一组数据，比如：2，5，10，0......

#要对这组数据进行排序，然后输出

```
spam=[]
while True:
   num=input()
   if num=='':
     break
   num=int(num)
   spam=spam+[num]
spam.sort()
print(spam)
```

