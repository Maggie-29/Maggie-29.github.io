# Chapter 5 Dictionary

## 5.1 字典数据类型

字典像列表一样，是许多值的集合，但他们也有区别：

1. 字典的索引可以使用不同的数据类型（不只是整数），而列表的索引（下标）只能是数字
2. 字典中的表项是不排序的，但在字典中，表项是有顺序，有它固定的位置的
3. 字典不可以像列表那样切片

一般来说，字典使用起来更灵活，不需要考虑下标，只需要考虑键-值对

```
birthdays={'Alice':'April 1','Bob':'Dec 12','Carol':'Mar 4'}

while True:
    print('Please enter a name: (blank to quit)')
    name=input()
    if name=='':
        break
    if name in birthdays:
        print(name+"'s birthday is "+birthdays[name])
    else:
        print('What is their birthday?')
        bday=input()
        birthdays[name]=bday
        print(name+"'s birthday is "+birthdays[name])
```



### 5.1.2 keys(),values()和items()

```
spam={'color':'red','age':42}
for v in spam.values():  #取了字典里所有的值 values
    print(v)
------------------------------------------------------------------------------------------
red
42
```

```
spam={'color':'red','age':42}
for k in spam.keys():  #取了字典里所有的键 keys
    print(k)
------------------------------------------------------------------------------------------
color
age
```

```
spam={'color':'red','age':42}
for i in spam.items():  #取了字典里的键-值对 key-value pairs
    print(i)
------------------------------------------------------------------------------------------
('color', 'red')
('age', 42)
#输出的是（）扩起来的是包含键和值的元组（tuple）
#元组可以被理解为是一种只能读不能随意修改的list（不过可以在定义的位置修改）
```

如何将字典的键 值 或 键-值对 以列表的形式返回

```
spam={'color':'red','age':42}
spam.keys()
------------------------------------------------------------------------------------------
dict_keys(['color', 'age'])
#如果想真正返回一个列表，可以在spam.keys()的外面加一个list()  e.g. list(spam.keys())
#那么输出结果就会是['color','age']
```



### 5.1.3 用in或not in检查字典中是否存在键或值

如果你输入的关于检查字典中是否有某值的语句是正确的，那么返回值就会是True，反之为False

### 5.1.4 get方法  #读取值

dictionaryName.get(a,b)   a为你想要取得值对应的键，b为如果a不在字典中，所要返回的默认值

```
picnicItems={'apples':5,'cups':2}
print('I am bringing '+str(picnicItems.get('apples',0))+' apples.')
print('I am bringing '+str(picnicItems.get('eggs',0))+' eggs.')
------------------------------------------------------------------------------------------
I am bringing 5 apples.  #'apples'在字典中，所以取这个键对应的值：5
I am bringing 0 eggs.    #'eggs'不在字典中，所以会返回默认值：0
```



### 5.1.5 setdefault  #存储

```
picnicItems={'apples':5,'cups':2}
print('I am bringing '+str(picnicItems.setdefault('eggs',0))+' eggs.')
print(picnicItems)
------------------------------------------------------------------------------------------
I am bringing 0 eggs.
{'apples': 5, 'cups': 2, 'eggs': 0}
```

小例题：统计一句话中所有character出现的次数

```
message = 'It was a bright cold day in April, and the clocks were striking thirteen.' 
count={}  #建立一个空字典
for character in message:
    count.setdefault(character,0)    #在给字典加character这个key之后，给它设定0这个值，以便之后对它进行自增
    count[character]=count[character]+1  #每遇到一次相同的character，就给字典中这个character对应的值加1
    
print(count)
------------------------------------------------------------------------------------------
{'I': 1, 't': 6, ' ': 13, 'w': 2, 'a': 4, 's': 3, 'b': 1, 'r': 5, 'i': 6, 'g': 2, 'h': 3, 'c': 3, 'o': 2, 'l': 3, 'd': 3, 'y': 1, 'n': 4, 'A': 1, 'p': 1, ',': 1, 'e': 5, 'k': 2, '.': 1}
```

## 		

## 5.2 漂亮打印

```
import pprint

#你的代码...

pprint.pprint(你想输出的结果) or print(pprint.pformat(你想输出的结果))  
#以上这两种代码的写法是等价的 都可以让你字典的输出更整洁有序
```

## 		

## 5.3 使用数据结构对真实世界建模

井字棋

```
theBoard = {'top-L': ' ', 'top-M': ' ', 'top-R': ' ', 'mid-L': ' ', 'mid-M': ' ', 'mid-R': ' ', 'low-L': ' ', 'low-M': ' ', 'low-R': ' '} 
def printBoard(board):  #board是个形式参数
    print(board['top-L'] + '|' + board['top-M'] + '|' + board['top-R'])
    print('-+-+-')
    print(board['mid-L'] + '|' + board['mid-M'] + '|' + board['mid-R'])     
    print('-+-+-')     
    print(board['low-L'] + '|' + board['low-M'] + '|' + board['low-R']) 
turn = 'X' 
for i in range(9):
    printBoard(theBoard)   #先打印棋盘（打印的其实是上一次运行的结果） 再落子 
    print('Turn for ' + turn + '. Move on which space?')
    move = input()
    theBoard[move] = turn
    if turn == 'X':
        turn = 'O'     
    else:  
        turn = 'X' 
printBoard(theBoard) #前面已经打印过了9次了，在循环结束后要再打印一次显示结果
```

### 		

### 5.3.2 嵌套的字典和列表

```
allGuests={'Alice':{'apples':5,'pretzels':12},
           'Bob':{'ham sandwiches':3,'apples':2},
           'Carol':{'cups':3,'apple pies':1}}
def totalBrought(guests,item):    #把常用的功能设置为一个函数
    numBrought=0
    for k,v in guests.items(): #k是人名，v是k带的items的字典
        numBrought=numBrought+v.get(item,0)  #加上v这个字典中某一item（key）对应的value
    return numBrought

print('Number of things being brought:')
print(' - Apples '+str(totalBrought(allGuests,'apples')))
print(' - Cups '+str(totalBrought(allGuests,'cups')))
print(' - Cakes '+str(totalBrought(allGuests,'cakes')))
print(' - Ham Sandwiches '+str(totalBrought(allGuests,'ham sandwiches')))
print(' - Apple pies '+str(totalBrought(allGuests,'apple pies')))
------------------------------------------------------------------------------------------
Number of things being brought:
 - Apples 7
 - Cups 3
 - Cakes 0
 - Ham Sandwiches 3
 - Apple pies 1
```

