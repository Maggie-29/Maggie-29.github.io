# Chapter 2 控制流

控制流相当于你思考问题时的思维逻辑 可以用流程图来表示

## 2.5 控制流的元素

条件（求值为布尔值Boolean（True or False）的语句)+代码块（缩进增加的语句）		

​		

## 2.7 控制流语句

### 2.7.1 if语句

if语句会在求值为True时执行，为False时跳过

Indentation 不能用tab，而是按四个空格

### 2.7.2 else语句

只有if条件为False时，才会执行else子句

### 2.7.3 elif语句

如果if条件为False，后面elif则会被运行，它提供了更多可能的条件

一旦有一个elif的语句求值为True，后面的条件就都会跳过

如果我们在最后的elif语句后加上else语句，我们就能保证至少有一个子句（且只有一个）会执行

​		

**#使用if，elif，else时的规则：**

1. 只能有一个if语句
2. elif语句都应该跟在if之后
3. 如果想要确保至少有一条子句被执行，在最后加上else语句



if和elif语句之间不能有其他同级语句，不然会报错（不符合上述第二条规则）

```
if 2<1:
    print('1<2')
elif 3>4:
    print('3>4')
print('Here!')
elif 3==3:
    print('Right!')
--------------------------------------------------------------------------------------
     elif 3==3:
       ^
SyntaxError: invalid syntax
```





### *Complex condition

```
# nesting if statements （在if语句里嵌套if语句）
if gpa>=0.85:
    if lowest_grade >= 0.70:
        print('Well done')

#And statements
if gpa>=0.85 and lowest_grade >= 0.70:
    print('Well done')


if gpa>=0.85 and lowest_grade >= 0.70:
    honour_roll=True
else:
    honour_roll=False  #somewhere later in your code
if honour_roll:     #honour_roll是一个标志位（一个flag） 求值为True或False
    print('Well done')

```

​		

### *elif和or的区别

```
if a or b:
#只要a或b任意一个为True,if语句后的内容就会被执行
--------------------------------------------------------------------------------------
if a:
    ....
elif b：
    ....
#a求值为True或b求值为True可以有不同的运行指令
```





### 2.7.4 while循环语句

可以对你的指令按照你限定的条件进行循环

##### 如何用break跳出while循环

```
while True:  #是个无限循环
    print('Please type your name')
    name=input()
    if name=='your name': #只有在if后面的条件成立时，循环才会结束
        break   #遇到break就会跳出while循环，也不再会执行break之后的语句了
print('Thank you')

```

​		

例题：验证姓名（'Joe'）和密码（'swordfish'）

```
while True:
    print('Who are you?')
    name=input()
    if name!='Joe':
        continue  #不运行下面的代码 而是跳到while循环的一开始
    print('Hello,Joe. What is the password?(It is a fish)')
    password=input()
    if password=='swordfish':
        break  #跳出while循环，运行接下来与while循环同一等级的print（）
print('Access granted')
```

一个等效的写法如下：

```
while True:
    print('Who are you?')
    name=input()
    if name=='Joe':  #主要是这一步与前一种写法不太一样，所以之后嵌套的语句会有一些变化
        print('Hello,Joe. What is the password?(It is a fish)')
        password=input()
        if password=='swordfish':
            break
print('Access granted')
```

### 		

### 2.7.8 for循环和range()函数

for循环都可以用while改写

但不是所有的while语句都能改写为for循环，比如while True语句

```
range(start, stop, step)  #给range加参数的规则 
#start的参数可以被取到，stop的参数不可以被取到 用数学集合的符号来表示就是[start, stop)
#step既可以是正数，也可以是负数
```

​		

例题1：求0到111之间所有偶数的和

方法一：

```
total=0
for num in range(0,111,2):
    total=total+num
print(total)
--------------------------------------------------------------------------------------
3080
```

方法二：

```
spam=[]
for i in range(0,111,2):
    spam.append(i)
print(sum(spam))
--------------------------------------------------------------------------------------
3080
```



​		

例题2：

```
#打印出
******
*****
****
***
**
*
```

```
for i in range(6,0,-1):  #从6开始，每次以此减1，直到减到1为止（不能取到stop的0那个值）
    print('*'*i)
------------------------------------------------------------------------------------   
******
*****
****
***
**
*
```



课后练习：

使用random.randint计算掷骰子出现2的概率 （使用for循环）