# Chapter 4 List

## 课后习题讲解

#### 1. Write a Python program to convert a list of multiple integers into **a single integer**.

#### Sample list: [11, 33, 50]       Expected Output: 113350				

写法一：

```
result=[] #result是一个list
spam=[11,33,50]
for i in range(len(spam)):
      result=result+str(spam[i]) 
      print(result)
----------------------------------------------------------------------------
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
----------------------------------------------------------------------------
113355
#错误提示：虽然代码跑通了，输出结果看上去也是对的，但依旧不符合题目要求（result此时的形式是str，并非int）

#修改方法：把最后一步 print(result) 改为 print(int(result))
```

​		

写法二：

用数学加法 我们也可以把列表中每一个值取出为str 再一个个相加 转int

​		

#### 2. Write a Python program to find the list in a list of lists whose sum of elements is the highest. 

#### Sample lists: [1,2,3], [4,5,6], [10,11,12], [7,8,9]  Expected Output: [10, 11, 12]

```
spam=[[1,2,3], [4,5,6], [10,11,12], [7,8,9]]
print(max(spam,key=sum))
print(sum(max(spam,key=sum)))
----------------------------------------------------------------------------
[10, 11, 12]
33
```

key 关键词可以用来指定一个function，设定了我们想要的处理数据的规则，这道题中用到的是sum这个function，计算出每个list中的子list元素的和，然后再取maximum，返回预期的和最大的子list。



#### 5. 用户输入一串数字，例如：1，10，-1，9...

#### &#160;&#160;&#160;&#160;在输入框直接回车作为输入结束（参照catName部分的代码）

#### &#160;&#160;&#160;&#160;输入一串代码将这些数据储存在一个list变量中

#### &#160;&#160;&#160;&#160;print用户输入的最大值，最小值及list排序结果

```
spam=[]
while True:
   num=input()
   if num=='':
     break
   num=int(num)
   spam=spam+[num]
print(max(spam))    #print用户输入的最大值
print(min(spam))    #print用户输入的最小值
spam.sort()         #对spam列表进行排序
print(spam)         #print顺序排序后的spam列表
```

​		



### 4.1.7 用del语句从列表中删除值

```
spam=['cat','rat', 'bat','elephant']
for i in range(len(spam)):
    del spam[i]
----------------------------------------------------------------------------
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

​		

除了第一个方法index( )是查看一个值在列表中的下标之外，其余方法在以 "列表名.方法名 ( )"  的形式被调用后可以直接修改列表 （以append（）为例）

```
spam=['rat','bat','cat']
spam.append('cat')
spam
----------------------------------------------------------------------------
['rat', 'bat', 'cat', 'cat']
```

但要注意不能写成 "列表名=列表名.方法名" 

因为这是在把你所使用方法( append( ) )的返回值 赋给之前的列表名，所以当我们再次查看列表名的值的时候 会得到None这个结果（方法的返回值）

```
spam=['rat','bat','cat']
spam=spam.append('cat')
print(spam)
----------------------------------------------------------------------------
None
```

  		



### 补充sort( )的用法

1. 如果列表中既有str这种数据类型，也有int这种数据类型，Python会无法比较不同的值对他们进行排序

2. list.sort ( ) 将列表值按ascii码进行排列  顺序为：数字、大写字母、小写字母

3. list.sort (reverse=True) 按ascii码逆序排序 顺序为：小写字母、大写字母、数字

   ​	

   #### 	
   
   #### Max（）函数的用法

#### 可以通过比较spam列表中子列表的元素，取出元素最大的子列表（会先比较子list中的第一个元素的大小，如果第一个元素相同，就会比较第二个元素的大小，以此类推）

```
spam=[[10,0,0],[2,9,2],[3,6,9],[8,9,9]]
print(max(spam))
----------------------------------------------------------------------------
[10, 0, 0]
#spam中四个子列表中第一个元素分别是10，2，3，8  最大为10
```

```
spam=[[2,8,9],[2,0,0],[2,9,8]]
print(max(spam))
----------------------------------------------------------------------------
[2, 9, 8]
#如果子列表中第一个元素相同，那么就会比较第二个元素的大小（分别是8，0，9），最大值是9，所以最后的运行结果是第二个元素为9的子list
```



1. #### 把A、B、C、D四位同学的成绩进行排序

```
def getv(x):
     return x[1]
spam=[['A',89],['B',90],['C',80],['D',85]]
spam.sort(key,getv)
spam
```



### 随堂小练习

