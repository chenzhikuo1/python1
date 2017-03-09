# -*- coding: utf-8 -*-
#"""为多行注释
"""
Created on Tue Feb 21 23:12:37 2017

@author: Administrator
"""
#python3.6如何安装第三方库：
#在cmd模式下输入:easy_install-3.6 库名 如easy_install-3.6 PyMySQl
#或者在在cmd模式下输入:pip install 库名 如pip install PyMySQl

#若见到$开始的命令，则在cmd模式下输入$后面的命令
#Ipython命令
#reset 重置所有变量 
#quit 退出ipyton
#env 显示环境变量 
#Ctrl+L 清除当前你所看到的屏幕，但并没有清除屏幕里的东西
#pwd 返回当前工作目录（字符串形式） 
#hist 打印命令的输入（可选输出）历史
#run *.py  *表示函数名，运行此函数
#前缀r或R表示“自然字符串”
####################变成注意事项#################################
#注意空格格式要统一：下一行对齐方式：关键字字数+一个空格 比如
#def func:
#    s=7;
#    for t in range[1:10]:
#        while x==0:
#              y=23

#run和debug的比较
#run是运行程序，在此模式下，断点，单步运行等都不起作用
#debug时，先设置好断点，点击debug进入调试模式，然后点击continue，程序运行到断点处
from collections import namedtuple
from numpy import *    #将Numpy库中所有函数都导入
#numpy所包含的函数：linspace(0,10,25) 0到10一共25个数据;random.rand(5,5)生成5*5矩阵，随机值在0到1之间
#zeros((3,3))3*3的0矩阵;ones((3,4)) 3*4都是1的矩阵;real(C),image(C)获得复数的实部和虚部;
#sum()求和;cumsum()累加;cumprod()累乘;mean()求平均值;average()求平均(无out，dtype参数，有weight参数);
#sort()排序函数std()标准差;var()方差;min()最小值;max()最大值pt;p()最大最小之差;argmax()最大值下标;
#argmin()最小值下标;sign()符号函数;uniqu()对数组从小到大排序，并只保留数组中不同的值。
#roots()计算多项式的根;poly()将根转换为多项式的系数;poly1d([1, 2, 0,-4,6])根据多项式系数生成多项式 
#polyfit()可以对一组数据进行多项式拟合
def arrayOperate():
    arr0= eye(3, dtype = int)   #生成3阶单位数组
    arr1=ones((3,4));   #生成3*4的全1数组
    arr2=zeros((3,3));  #生成3*3的全0数组
    arr3=linspace(0,10,5)  #生成范围0-10的长度为5的浮点数数组
    arr4=arange(0,8,3)    #生成范围0-8的步长为3的整数数组
    arr5=empty((4,2))  #生成4*2的随机数组 
    arr6=array([1,2,6,4,6,5,0,4])              #生成内容为[1,2,6,4,6,5,0,4]的一维数组
    [arr,index]=unique(arr6,return_index=True) #arr为保留的数组内容，index为数字第一次出现的位置
    cumsum(arr6)              #求数组的累加和
    cumprod(arr6)              #求数组的累乘积
    arr7=array([[1,2,4],[3,4,6]])#生成内容为[1 2 4;3 4 6]的二维数组
    arr8=array([[3,1,4],[2,1,3]])#生成内容为[3 1 4;2 1 3]的二维数组
    arr7/arr8         #两数组形状相同，实际上是点除
    arr7*arr8         #两数组形状相同，实际上是点乘
    arr7+arr8         #两数组形状相同，实际上是每个元素相加
    transpose(arr7) #数组的转置
    size(arr7,0)   #获取数组的行数
    size(arr7,1)   #获取数组的列数
    mat1=mat([[1,1],[2,3],[4,2]])
    size(mat1,0)   #获取矩阵的行数
    size(mat1,1)   #获取矩阵的列数
    average(mat1,0)  #求每一列的平均值
    mat2=mat(eye(2),dtype=int);  #生成二维单位矩阵
    mat3=mat(zeros((3,1)),dtype=int);  #生成3*1零矩阵
    combineOfHor=hstack((mat1,mat3))   #将矩阵水平连接即增加列数
    combineOfVer=vstack((mat1,mat2))   #将矩阵垂直连接即增加行数
    mat4=mat(ones((2,3)),dtype=int);  #生成2*3全1矩阵
    mat5=mat(diag(mat4));          #获取矩阵的对角线元素
    mat6=mat([[1,1,0],[0,2,3]])
    sumOfCol=mat6.sum(0)  #求矩阵每一列的和
    sumOfRow=mat6.sum(1)  #求矩阵每一行的和
    sumMat=mat6.sum()   #求整个矩阵的和
    mat6[:1].max()   #求矩阵第二列的最大值
    mat6[0:].max()   #求矩阵第一行的最大值
    sumRow=mat6.sum(axis=1)  #求矩阵每一行的和
    maxOfCol=mat6.max(0);      #求所有列的最大值
    minOfRow=mat6.min(1);      #求所有行的最小值

    newMat=mat1*mat6    #两矩阵相乘
    mat7=mat([[1,2],[3,2]])
    invMat7=mat7.I   #求矩阵的逆
    transMat7=mat7.T   #求矩阵的转置
    conjMat7=mat7.H   #求矩阵的共轭转置
    mat8=multiply(mat7,transMat7)    #矩阵的点乘
    print(mat8)
arrayOperate()
def polyOperate():
     coeff = [1,2,-1,-2]  #求多项式x^3+2x^2-x-2的根
     roots(coeff)
     poly((2,3))            #求两个根分别为2和3的多项式
     poly1=poly1d([1, 2, 0,-4,6],variable='x')   #生成多项式x^4+2x^3-4x+6
     poly2=poly1d([1, 0,-1])     ##生成多项式x^2-1
     poly1(5)     #求x=5时多项式的值
     poly1.r      #求多项式的根
     poly1.c      #输出多项式的系数
     poly1.order      #输出多项式的最高阶数
     poly1*poly2      #两个多项式相乘
     poly1/poly2      #两个多项式相除
     poly1-poly2      #两个多项式相减
     poly1.deriv()   #对多项式进行求导
     poly1.integ()   #对多项式进行求积分
def stringOperate():
    #如果一个文本字符串在一行放不下, 可以使用圆括号来实现隐式行连接:
    text=("i wrote your name in the sky, but the wind blew it away; I wrote your name in the" 
    "sand, but the waves washed it away; I wrote your name in my heart, And forever it will stay.") 
    #为多行字符串使用三重双引号"""而非三重单引号'''
    letters="""i wrote your name in the sky, but the wind blew it away;
    I wrote your name in the sand, but the waves washed it away; 
    I wrote your name in my heart, And forever it will stay."""
    #注释：
    #为了提高可读性, 注释应该至少离开代码2个空格.注释不需要列对齐
    x=3;y=4  #可以在同一行中使用多条语句，语句之间使用分号(;)分割。
    a=letters[-5]  #取字符串倒数第5个元素
    print(len(letters))  #获得字符串的长度
    letters[4::3]  #从头到尾每隔3个元素，输出一个
    letters[:]  #取字符串所有元素
    letters[-1::-2]  #从倒数第一个元素开始，每隔一个输出元素
    letters
    letters.split(' ')  #将letters以' '为分隔符，将字符串转化为字符串列表
    firstAppear=letters.find('your')   #从字符串中找“your”,并返回第一次出现的位置
    lastAppear=letters.rfind('your')   #从字符串中找“your”,并返回最后一次出现的位置
    times=letters.count("name")   #统计"name"出现的次数
    lastAppear
    letters.strip(' ')#移除字符串头尾的空格
    letters.rstrip(' ')#移除字符串末尾的空格
    letters.capitalize()#大写字符串第一个字符
    str=letters.upper()#大写字符串所有字符
    letters.swapcase()#对字符串的大小写字母进行转换
    letter1="I wrote your name in the sky, but the wind blew it away"
    letter1.isupper()   #如果这个字符串的所有字符全为大写且至少有一个字符，则返回true
    letter1.isdigit()   #如果这个字符串的所有字符全为数字字符且至少有一个字符，则返回true
    letter1*2#重复输出字符串
    "name" in letter1 #判断"name"是否在字符串中，返回bool型
    "name" not in letter1 #判断"name"是否在字符串中，返回bool型
    letter1.center(60,' ')#返回一个原字符串中心对齐,并使用空格(默认为空格)填充至指定长度的新字符串。如果指定的长度小于原字符串的长度则返回原字符串。
    letter1.ljust(60,' ')#返回一个原字符串左对齐,并使用空格(默认为空格)填充至指定长度的新字符串。如果指定的长度小于原字符串的长度则返回原字符串。
    letter1.rjust(60,' ')#返回一个原字符串右对齐,并使用空格(默认为空格)填充至指定长度的新字符串。如果指定的长度小于原字符串的长度则返回原字符串。
    letter1.replace('wrote','wr')#将字符串中的所有wrote替换为wr
    #将字符串中前两个name替换为Name,若字符串出现的次数小于指定的次数，则将所有的都替换了
    print(letters.replace('name','Name',2))
#函数与函数间定义空一行
def stringlist():
    #python的列表操作
    weekdays=["monday","tuesday","wednesday","thursday"]
    weekday=("monday","tuesday","wednesday","thursday")#创建一个元组
    list(weekday)#将元组元素转化为列表
    weekdays[-2]#取列表的倒数第二个元素
    weekdays[::2]#从头到尾每隔一个元素取一次
    weekdays.append("friday")#在weekdays末尾添加一个元素
    fr=["saturday","sunday"]
    weekdays.extend(fr)#将weekdays和fr合并，注意和append用法的不同，extend是合并两个列表
    weekdays.insert(1,"Friday")#向weekdays第二个元素插入一个
    weekdays.reverse()#将列表中元素反向
    del weekdays[0]#删除weekdays第一个元素
    weekdays.remove("saturday")#移除指定的元素，注意和del的区别
    #注意列表无push操作
    weekdays.pop()#弹出列表中最后一个元素或者weekdays.pop(-1)
    weekdays.pop(0)#弹出列表中第一个元素
    print("Tuesday索引是:",weekdays.index("tuesday"))#返回字符串"sunday"的索引
    weekdays.insert(2,"friday")
    weekdays.count("friday")#计算friday出现的次数
    str1='-'
    week=str1.join(weekdays)#将序列中的元素以"-"字符连接生成一个新的字符串
    week.split(str1)#将字符串以"-"分离
    "sunday" in weekdays#判断sunday是否在列表中
    max(weekdays)#求列表的最大值
    min(weekdays)#求列表的最小值
    sortedWeekdays=sorted(weekdays)#对weekdays进行排序
    weekdays.sort(reverse=True)#对weekdays进行逆序排列
    #Week=weekdays#若直接赋值，此时若对weekdays做任何改变，都会影响到week,反之亦然
    #而若下面三种复制方式时，此时对weekdays做任何改变，都不会影响到week    
    Week=weekdays.copy()
    #Week=weekdays[:]
    #Week=list(weekdays)
    print(weekdays)
    fruit1=["apple","organge"]
    fruit2=[1,"banada",2,"lemon"]#列表中允许不同类型的元素共存
    fruits=[fruit1,fruit2,"pear"]
    fruits[0]#取fruits中第0个元素
    fruits[1][1]#取fruits中第二个元素中的第二个子元素即"banada"
    numList=list(range(1,5))#使用range函数建立一个列表
    numList1=[number-1 for number in range(3,8)]#建立一个内容从2到6的列表
    sum(numList1)#求列表元素之和
    rows=range(1,4)
    cols=range(0,2)
    numList2=[(row,col) for row in rows for col in cols]#建立一个内容从2到7的列表
    #python使用缩进来表示代码块，不需要使用大括号({})。缩进的空格数是可变的，但是同一个
    #代码块的语句必须包含相同的缩进空格数。
    for nn in numList2:
        print(nn,end=" ")
    print()#换行
    #print ("weekdays列表:", weekdays)#打印列表
    
def stringtuple():
        #python的元组操作 
        #python 的元组与列表类似，不同之处在于元组的元素不能修改。元组使用小括号，列表使用方括号。
        #创建一个元组,两种方式都对
        #month="January","February","March","April","May","June"
        tup1 = (50,);#元组中只包含一个元素时，需要在元素后面添加逗号
        del tup1;#删除整个元组
        month=("January","February","March","April","May","June")
        month1=["January","February","March","April","May","June"]
        month=tuple(month)#将列表转化为元组
        numTup=(12,23,4,22,54)
        print(numTup[-1])#打印元组的倒第一数个元素
        max(numTup)#返回元组最大元素
        min(numTup)#返回元组最小元素
        print("该元组长度为:",len(numTup))#打印元组的元素个数
        #定义一个namedtuple类型Person，并包含name，sex,age,number属性。
        Person=namedtuple('Person',['name','sex','age','number'])
      
        Mary=Person("Mary","woman",12,20133333)
        Jacson=Person("Jacson","man",34,20148838)
        Rose=Person("Rose","woman",24,20154883)
        #通过对象访问nametuple类型的Person，类似于类对象的使用
        for person in[Mary,Jacson,Rose]:
            print("%s:性别%s,年龄%d,学号%d" %(person.name,person.sex,person.age,person.number))
def stringdict():
     #python的字典操作 
     #字典是另一种可变容器模型，且可存储任意类型对象。字典的每个键值(key=>value)对用冒号(:)分割，
     #每个对之间用逗号(,)分割，整个字典包括在花括号{}中。字典中的键必须唯一
     tol=["ab","cd","ef"]#创建一个列表
     print(dict(tol))#将列表转化为字典
     tup=(["a","b"],["c","d"])
     dict(tup)#将元组转化为字典
     strdict = {'Alice': '2341', 'Beth': '9102', 'Cecil': '3258'}#创建一个字典
     strdict["Gillan"]="2328"#向字典中添加一个新元素
     strdict["Gillan"]="2748"#若字典中已有键时，新添加的键值将会覆盖原有的键值
     strdict1={'John': '4841', 'Eric': '1092'}
     #将strdict1中的元素添加到strdict中，若strdict中已有strdict1中的元素，则strdict1中对应的
     #键值会替换掉strdict中的键值
     strdict.update(strdict1)
     del strdict['Alice']#删除strdict中对应的元素
     #strdict.clear()#删除字典中所有元素
     'Alice' in strdict#判断'Alice'对应的键值是否在字典中
     strdict.get("Gillan")#获得"Gillan"键值对应的元素，若字典中不存在此键值，则返回None
     keys=strdict.keys()#获得字典的所有键值
     valueList=list(strdict.values())#获得字典的所有值并转化为列表
     copyDict=strdict#若直接赋值，此时若对strdict做任何改变，都会影响到copyDict,反之亦然
     copyDict1=strdict.copy()#若使用copy()函数赋值，此时若对strdict做任何改变，都不会影响到copyDict
     print(strdict)
     words="letters"
     #统计字符串中各字符出现的次数并保存在字典中
     letter_count={letter: words.count(letter) for letter in words}
     
def Set():
     #set集合像字典一样，只是只有键，没有值，并且集合中的元素必须唯一     
     numSet1={3,2,4}
     numSet2={4,5}
     #求两个set的交集
     numSet1&numSet2
     numSet1.intersection(numSet2)
     #求两个set的并集
     numSet1|numSet2
     numSet1.union(numSet2)
      #求两个set集合不同的元素,返回前面一个集合中的不同元素
     print(numSet1-numSet2)
     numSet1.difference(numSet2)
     #求两个set集合不同的元素,返回两个集合中的不同元素的集合
     numSet2^numSet1
     numSet1.symmetric_difference(numSet2)
     #判断前一个集合是否是后一个集合的子集
     print(numSet1<=numSet2)
     numSet1.issubset(numSet2)
      #判断前一个集合是否是后一个集合的父集
     print(numSet1>=numSet2)
     numSet1.issuperset(numSet2)
     
def structureOperate():
    #'\'为继续操作符
    n=1+2+ \
    3
    print(n)
    #input函数用于输入
    age = int(input("请输入你家狗狗的年龄: "))
    if age < 0:
    	 print("你是在逗我吧!")
    elif age == 1:
    	 print("相当于 14 岁的人。")
    elif age == 2:
    	 print("相当于 22 岁的人。")
    elif age > 2:
    	 human = 22 + (age -2)*5
    	 print("对应人类年龄: ", human)
        
     #求1到num的和
    num = int(input("输入一个整数: "))
    i=1
    sum1=0
    while i<=num:
        sum1+=i
        i+=1
    print("求1到%d的和为："%(num),sum1)#输出求和的结果
    languages = ["C", "C++", "Perl", "Python"] 
    for sub in languages:
        if sub=="C++":
          print("此数组中含有元素：",sub)
          break
    #若使用for循环打印数字序列，可以使用内置range()函数，从0开始
    for j in range(0, 10, 3) :#0-10为范围，3为步长。默认步长为1
        print(j)
    for p in range(0,len(languages)) :#范围为0-(len-1)，3为步长。默认步长为1
        print(languages[p],end=" ")#print默认是以\n结尾，即换行，将其改为空格
    print()#输出一个换行符
    days=["monday","tuesday","wednesday","thursday"]
    nums=[1,2,3,4]
    #使用zip函数可同时迭代多个序列，当最短的序列遍历完时，停止循环
    for day,num in zip(days,nums):
        print(day,":",num)
        
 #函数操作  
#形参带默认值的函数     
def menu(wine,entree,dessert="pudding"):
    return{"wine": wine,"entree":entree,"dessert":dessert}#返回字典的值
#带不定长参数的函数。加了星号（*）的变量名会存放所有未命名的变量参数
#此函数调用时，至少含有两个参数，以赋予arg1和arg2,若有剩余则执行for循环
def printinfo(arg1,arg2, *vartuple ):
   print ("输出: ")
   print("arg1=",arg1)
   print("arg2=",arg2)
   for var in vartuple:
      print (var)   
      
#**表示的形参表示参数为一个字典
def printDict(**vardict ):
   print ("输出: ",vardict)
   
#定义一个求和函数
def add_args(arg1,arg2):
    return arg1+arg2

#定义一个参数为形式函数为函数的函数
def runSomething(func,arg1,arg2):
    Sum=func(arg1,arg2)
    return(Sum) #return sum也对
    
#定义一个求阶乘函数
def multply_args(*args):
    chengji=1
    for var in args:
        chengji*=var  
    return chengji

#定义一个形参为函数和列表元素的函数
def runWithPositionalArgs(func,*args):
    res=func(*args)
    return res

#定义一个带内部函数的函数
def knights(saying):
    def inner(quote):
        return "We are the knights who say "+quote
    return inner(saying)

#用关键字lambda定义一个匿名函数,Captialize相当于函数名
Captialize=lambda word:word.capitalize()+'!'

def EditWords(*words):
    for pp in words:
        #word为参数，分号后表示执行的操作
        print(Captialize(pp))
        
#生成器(generator):使用了yield的函数被称为生成器（generator）。跟普通函数不同的是，生成器是一个返回迭代器的
#函数,只能用于迭代操作，更简单点理解生成器就是一个迭代器。在调用生成器运行的过程中，每次遇到
#yield时,函数会暂停并保存当前所有的运行信息，返回yield的值。并在下一次执行 next()方法时从当前位置继续运行。
def fibonacci(n): # 生成器函数 - 斐波那契
    a, b, counter = 0, 1, 0#对变量分别进行赋值
    while True:
        if (counter > n): 
            return
        yield a
        a, b = b, a + b#逗号表达式，分别进行赋值
        counter += 1
        
#装饰器(decorators):装饰器是一个函数,一个用来包装函数的函数，装饰器在函数申明完成的时候被调用，调用之后
#返回一个修改之后的函数对象，将其重新赋值原来的标识符，并永久丧失对原始函数对象的访问
#(申明的函数被换成一个被装饰器装饰过后的函数)。当我们对某个方法应用了装饰方法后， 其实就改变了被装饰函数
#名称所引用的函数代码块入口点，使其重新指向了由装饰方法所返回的函数入口点。由此我们可以用decorator改变
#某个原有函数的功能，添加各种操作，或者完全改变原有实现   
def salesgirl(discount):
    def expense(method):
        def serve(*args):
            print("售货员:您好，请问需要什么?", method.__name__)#注意是两横"__"
            res = method(*args)
            if res:
                print("售货员:这双鞋原价300元.现在换季，可以打%d折" %(discount))
            else:
                print("售货员:好吧，试试另一款呢?")
            return res
        return serve#表示此函数调用完毕
    return expense
@salesgirl(8)
def tryThisShoes(size):
    if size < 35:
        print("我: %d码对我太小了" %(size))
        return False
    else:
        print("我:%d码对我正好" %(size))
        return True
result = tryThisShoes(37)
if result :
    result="是的"
else:
    result="不是的"
print("妈妈:你想买这个吗?")       
print("我:",result)

animal="tiger"#定义一个全局变量

def changeGlobal():
    #显性声明使用的是全局变量，若不声明则表示的是新声明的局部变量"animal"
    global animal
    animal="lion"
    #print("全局变量变为:",animal)
##调用函数前，打印此时的animal
#print("全局变量为:",animal)
#changeGlobal()
##调用函数后，再打印animal
#print("全局变量变为:",animal)       

#内建类型None表示一个空对象，没有方法和属性。None是一个特殊的常量。None和False不同。None不是0。
#None不是空字符串。None和任何其他的数据类型比较永远返回False。None有自己的数据类型NoneType。
#你可以将None复制给任何变量，但是你不能创建其他NoneType对象。
#print(__name__)#获得当前的函数名
#print(__loader__)#获得当前的模块名
#print(__package__)#获得当前的包名
#print(__doc__)#获得当前的文档说明
#print(__builtins__)#获得当前的内建模块名 

      
#调用函数
#start=time.clock()#程序开始时间
#f = fibonacci(10) # f 是一个迭代器，由生成器返回生成

#while True:
#    try:
#        print (next(f), end=" ")
#    #python常见错误类型
#    except StopIteration as error1:
    #except ArithmeticError as error1:#数值计算错误
    #except OverflowError	#数值运算超出最大限制
    #except ZeroDivisionError	#除(或取模)零 (所有数据类型)
    #except IOError	      #输入/输出操作失败:
    #except ImportError	 #导入模块/对象失败:
    #except IndexError	   #序列中没有此索引(index)
    #except KeyError	   #映射中没有这个键:
    #except NameError	   #未声明/初始化对象 (没有属性):
    #except SyntaxError	  #Python 语法错误:
    #except IndentationError	 #缩进错误
    #except ValueError	     #传入无效的参数
      #sys.exit()#退出系统
try:
    #打开一个文件
    fh = open("testfile","w")
    #向文件中写内容
    fh.write("这是一个测试文件，用于测试异常!")
except: #此种异常未指明异常的确切类型
    print("Error: 没有找到文件或读取文件失败。")
else:
    print("内容写入文件成功。")
    fh.close()  #关闭打开的文件

#导入总应该放在文件顶部, 位于模块注释和文档字符串之后, 模块全局变量和常量之前. 
#导入应该按照从最通用到最不通用的顺序分组:
#1、标准库导入;2、第三方库导入;3、应用程序指定导入
#导入plot模块,每个导入应该独占一行
#import plot
#plot.demo()#调用plot文件中的demo()函数
#从模块中导入一个指定的部分到当前命名空间并用别名count表示
from collections import Counter as count
lunch={"eggs","eggs","spam","eggs"}
print(count(lunch))

#从一个包中直接导入一个函数或者变量:
from math import pi
import math
#math包包含：sqrt(x)求x的平方根;ceil(x)取不小于x的最小整数;floor(x)求不大于x的正大整数;gcd(x,y)求最大公约数
#sin(),asin()等三角函数;pow()求冥次方;sqrt()求平方根;log2(x)求x的以2为底的对数;log(x)求x的以e为底的对数;
#log10(x)求x的以10位底的对数;exp(x)求e的x次幂;pi:π的值,radians(x):将角度转化为弧度；degrees(x)将弧度转化为角度
def randOperate():
    math.log(1024,2)#求log2(1024)的值
    math.factorial(3)  #求3的阶乘
    import random
    abs(-5.4)      #求绝对值
    random.choice(['apple', 'pear', 'banana'])#从三个元素中随机选一个
    random.sample(range(20), 5)#从0-19的范围中，随机选取5
    5*random.random()    #产生0-5的随机的浮点数
    random.randrange(6)#产生0-5的随机整数
    isinstance(5.3,int)  #判断5.3是不是整数，返回True或False
    isinstance(5.3,float)  #判断5.3是不是浮点数，返回True或False
def timeOperate():
    #datetime模块为日期和时间处理同时提供了简单和复杂的方法
    from datetime import date #导入日期的包
    now = date.today()#返回今天的时间
    #获取年月日
    now.year
    now.month
    now.day
    now.weekday()  #返回weekday，如果是星期一，返回0；如果是星期2，返回1，以此类推
    now.isoformat() #返回格式如'YYYY-MM-DD’的字符串；
    import time#导入时间模块的包
    time.time()#返回当前时间的时间戳（1970纪元后经过的浮点秒数）
    time.localtime()#获得本地的当前日期及时间
    time.strftime("%Y-%m-%d %X",time.localtime()) #以'YYYY-MM-DD HH:MM::SS’形式返回当前时间
    time.ctime(time.time()) #以星期 月 日 时:分:秒 年形式返回时间
def RegularExpressionOperate():   #正则表达式
    import unicodedata as ud
#    name=ud.name('a')  #输入一个unicode编码的字符，返回一个大写的字符名
    name=ud.name('\u4e25') #汉子"严"的unicode表示形式
    print(name)
    value=ud.lookup(name) #输入一个区分大小写的名字，返回一个unicode编码的字符
    guai='\N{CJK UNIFIED IDEOGRAPH-4E56}'  #当知道一个字符的名字unicode表示方示方式时，通过这种方式定义字符
    print(guai)
    #UTF-8编码规则
    #UTF-8的编码规则很简单，只有二条：
    #1）对于单字节的符号，字节的第一位设为0，后面7位为这个符号的unicode码。因此对于英语字母，UTF-8编码和ASCII码是相同的。
    #2）对于n字节的符号（n>1），第一个字节的前n位都设为1，第n+1位设为0，后面字节的前两位一律设为10。剩下的没有提及的二进制位，全部为这个符号的unicode码。
    snowman='\u2603'
    ds=snowman.encode('utf-8')  #使用utf-8方式编码
    snowman1=ds.decode('utf-8')
    print(snowman1)
    #使输出右对齐
    for x in range(1, 5):
        #注意下面的标号是从0开始，并且相邻元素有空格,'d'表示字符数据格式为整型
        print('{0:>2d} {1:>3d} {2:>4d}'.format(x, x*x, x*x*x))
#    #使输出左对齐
#    for k in range(1, 5):
#        print('{0:<2d} {1:<3d} {2:<4d}'.format(k, k*k, k*k*k))
#     #使输出居中对齐
#    for j in range(1, 5):
#        print('{0:^2d} {1:^3d} {2:^4d}'.format(j, j*j, j*j*j))
#    #使输出居中对齐,并使空白处用*填充
#    for j in range(1, 5):
#        print('{0:*^2d} {1:*^3d} {2:*^4d}'.format(j, j*j, j*j*j))
#    #使输出右对齐
#    for x in range(1, 5):
#        #repr()： 产生一个解释器易读的表达形式。
#        print(repr(x).rjust(2), repr(x*x).rjust(3), repr(x*x*x).rjust(4))
    #正则表达式的元字符有. ^ $ * ? { [ ] | ( )
    #．表示任意字符
    #[]用来匹配一个指定的字符类别，所谓的字符类别就是你想匹配的一个字符集，对于字符集中的字符可以理解成或的关系。
    #^ 如果放在字符串的开头，则表示取非的意思。[^5]表示除了5之外的其他字符。而如果^不在字符串的开头，则表示它本身。
    
                           
    #具有重复功能的元字符：
    #* 对于前一个字符重复0到无穷次
    #对于前一个字符重复1到无穷次
    #？对于前一个字符重复0到1次
    #元字符(|), 表示"或"
    #{m,n} 对于前一个字符重复次数在为m到n次，正则表达式优先匹配n,其中，{0,} = *,{1,} = , {0,1} = ?
    #{m,n}? 对于前一个字符重复次数在为m到n次，正则表达式优先匹配m,其中，{0,} = *,{1,} = , {0,1} = ?
    #{m} 对于前一个字符重复m次
    
     
    #^	匹配字符串的开头
    #$	匹配字符串的末尾。
    #\d 匹配任何十进制数；它相当于类 [0-9]。
    #\D 匹配任何非数字字符；它相当于类 [^0-9]。
    #\b	匹配一个单词边界，也就是指单词和空格间的位置。 'er\b' 可以匹配"never" 中的 'er'，但不能匹配 "verb" 中的 'er'。
    #\B	匹配非单词边界。
    #\s 匹配任何空白字符；它相当于类 [ fv]。
    #\S 匹配任何非空白字符；它相当于类 [^ fv]。
    #\w 匹配任何字母数字字符；它相当于类 [a-zA-Z0-9_]。
    #\W 匹配任何非字母数字字符；它相当于类 [^a-zA-Z0-9_]。
    #[aeiou]	匹配中括号内的任意一个字母
    #[0-9]	匹配任何数字。类似于 [0123456789]
    #[a-z]	匹配任何小写字母
    #[A-Z]	匹配任何大写字母
    import re  #导入正则表达式模块
     
    pattern = re.compile(r'hello')# 将正则表达式编译成Pattern对象
     
    # 使用Pattern匹配文本，获得匹配结果，无法匹配时将返回None
    result = pattern.match('hello world!')
    if result:  #如果result不为空时，则打印
        # 使用Match获得分组信息
       print(result.group())
    text = "Jay is a handsome boy"
    re.split(r'\s+', text)  #将字符串在空格处分离
    #re.match 尝试从字符串的起始位置匹配一个模式，如果不是起始位置匹配成功的话，返回None
    #re.match(pattern, string, flags=0)
    m=re.search("^a\w+","abcdfa\na1b2c3",re.M)  #search从字符串任意位置匹配一个模式，只要匹配到就返回,re.M表示多行匹配
    if m:
       print(m.group())
    #re.I(Ignorecase)	使匹配对大小写不敏感
    #re.L	做本地化识别（locale-aware）匹配
    #re.M(Multiple)	多行匹配，影响 ^ 和 $
    #re.S	使 . 匹配包括换行在内的所有字符
    #re.U(Unicode)	根据Unicode字符集解析字符。这个标志影响 \w, \W, \b, \B.
    #re.X	该标志通过给予你更灵活的格式以便你将正则表达式写得更易于理解。
    m=re.findall("^a\w+","abcdfa\na1b2c3",re.M)  #findall需要找到所有匹配的对象
    if m:
       print(m)
    #如果你需要匹配字符 "[" 或 "\"，你可以在它们之前用反斜杠来取消它们的特殊意义： \[ 或 \\
    #用于替换字符串中的匹配项。pattern : 正则中的模式字符串;repl : 替换的字符串，也可为一个函数。
    #string : 要被查找替换的原始字符串;count : 模式匹配后替换的最大次数，默认 0 表示替换所有的匹配。
    #re.sub(pattern, repl, string, count=0)                                    
    phone = "2004-959-559 # 这是一个电话号码"

    # 删除注释
    num = re.sub(r'#.*$', "", phone)  #用""替换掉#后面的所有字符
    print ("电话号码:", num)
    # 移除非数字的内容
    num = re.sub(r'\D', "", phone)
    print ("电话号码:", num)  
    source="I wish I may have a dish of fish tonight."
    re.findall('[wf]ish',source)        #首字符为w或f  
    re.findall('I (?!=may)',source)  #找到所有I 后面不为may的表达式
    re.findall('(?<=I) wish',source)  #找到所有 wish前面不为I的表达式
    print(re.search('tonight.\$',source))  #找到一个以tonight.为结尾的字符串      
def fileOperate():
    #python中对文件、文件夹（文件操作函数）的操作需要涉及到os模块和shutil模块。
    import os,stat
    os.getcwd()  #得到当前工作目录，即当前Python脚本工作的目录路径: 
    os.listdir()   #返回指定目录下的所有文件和目录名:
    #os.remove(r"C:\Users\Administrator\Desktop\load_data.xlsx")   #函数用来删除一个文件:
    #os.rmdir("E:\AndroidSDK")    #删除指定目录
    #os.removedirs("E:\AndroidSDK") #删除多个目录：
    #os.mkdir('E:\PythonProgram1')    #创建目录,注：创建已存在的文件夹将异常
    #os.makedirs("D:temp\home\month\day")   #创建多级目录.注：创建已存在的文件夹将异常
    os.path.isfile("testfile.txt") #检验给出的路径是否是一个文件：
    os.path.isdir('E:\PythonProgram')  #检验给出的路径是否是一个目录：
    os.path.isabs('E:\C++')   #判断是否是绝对路径：
    #返回是否是快捷方式
    os.path.islink('D:\迅雷影音\V5.1.25.4252')
    os.path.split("E:\PythonProgram\PythonOperate.py")   #返回一个路径的目录名和文件名
    os.path.splitext(r"PythonOperate.py")  #分离扩展名：
    os.path.dirname('E:\PythonProgram')      #获取路径名：
    os.path.basename('testfile.txt')     #获取文件名：
    os.path.exists('C:\Python25')     #检验给出的路径是否真地存在
    os.path.getatime("E:\PythonProgram\PythonOperate.py")  #文件或文件夹的最后访问时间
    os.linesep          #给出当前平台使用的行终止符
    #os.system('cmd') #运行shell命令.启动dos
    os.getenv('USERNAME')   #读取环境变量: os.putenv()   设置环境变量
    os.name      #指示你正在使用的平台 对于Windows，它是'nt'，而对于Linux/Unix用户，它是'posix'
    #os.rename('E:\software','E:\Software')  #对文件或目录进行重命名
    os.stat("PythonOperate.py")  #获取文件属性：
    os.path.abspath('testfile.txt')    #获得绝对路径。
    os.path.join("E:\PythonProgram", "pandas.py")  #连接目录和文件名。
    os.chmod("Tkinter1.py", stat.S_IWOTH)        #修改文件权限与时间戳：设置文件可以被其他用户写入
    os.path.getsize("PythonOperate.py")#获取文件大小  
    #os.chdir("E:\C++")    #将当前工作目录修改为E:\C++
    #os.chflags("E:\PythonProgram",1)   #设置路径的标记为数字标记。
                   
                   
    fp = open("testfile.txt", "w") 
    #关于open 模式：
    #二进制读取与文本读取的区别：用二进制模式打开一个文件的时候，文件本身的内容和你编写程序时用函数读到的
    #内容完全相同（或者说和磁盘上的内容完全相同);文本模式:操作系统在将文件内容传给上层程序（库函数，或者
    #是你的程序）时，或者上层程序通过操作系统向文件写入内容时，操作系统都会预先进行一层预处理（或者说转义），
    #具体过程依赖于操作系统的实现。除此以外，两种打开方式其实是大同小异的。
    #w     以写方式打开，
    #a     以追加模式打开 (从 EOF 开始, 必要时创建新文件)
    #r+    以读写模式打开
    #w+    以读写模式打开 (参见 w )
    #a+    以读写模式打开 (参见 a )
    #rb    以二进制读模式打开  
    #wb    以二进制写模式打开 (参见 w )
    #ab    以二进制追加模式打开 (参见 a )
    #rb+   以二进制读写模式打开 (参见 r+ )
    #wb+   以二进制读写模式打开 (参见 w+ )
    #ab+   以二进制读写模式打开 (参见 a+ )
    fp.name  #获取文件名
    poem='''If you were a teardrop in my eye, For fear of losing you,I would never cry. 
    And if the golden sun,Should cease to shine its light, Just one smile from you,Would make my whole world bright.'''
    fp.write(poem)      #把poem写到文件中，write()并不会在poem后加上一个换行符
    fp.close()       #关闭文件。关闭后文件不能再进行读写操作。
    fp = open("testfile.txt", "r") 
    size=40
    fp.read(size)       #size为读取的长度，以byte为单位,若没有size则读完全文
    #fileObject.seek(offset, whence)
    #将文件打操作标记移到offset的位置。这个offset一般是相对于文件的开头来计算的，一般为正数。
    #whence：可选，默认值为 0。给offset参数一个定义，表示要从哪个位置开始偏移；0代表从文件开头开始算起，1代表从当前位置开始算起，2代表从文件末尾算起。
    fp.seek(0,0)     #将文件操作标记移到文件开头        
    fp.readline()   #读一行，如果定义了size，有可能返回的只是一行的一部分；若没有size则读完一行
    #fp.next()   #返回文件的下一行
    print(fp.tell())   #返回文件操作标记的当前位置，以文件的开头为原点 
    #把文件每一行作为一个list的一个成员，并返回这个list。其实它的内部是通过循环调用readline()来实现的。
    #如果提供size参数，size是表示读取内容的总长，也就是说可能只读到文件的一部分。
    fp.seek(0)   #将文件操作标记移到文件开头 
    lines=fp.readlines()
    for line in lines:
        print(line,end='')   
    fp.flush()   #刷新文件内部缓冲，直接把内部缓冲区的数据立刻写入文件, 而不是被动的等待输出缓冲区写入。
    
            
    import csv,collections
    #使用reader和writer读写csv文件时，列默认由","分隔，行默认由线分隔
    with open('mycsv1', 'w',newline='') as fout:   #此时换行符为''即不会自动添加一行空格
         #writerr(csvfile, dialect='excel',fmtparam])
         #dialect编码风格，默认为excel方式; fmtparam格式化参数，用来覆盖之前dialect对象指定的编码风格。
         writer = csv.writer(fout,dialect='excel',)
         writer.writerow(['姓名', '年龄', '电话']) #向csv文件里写数据
         #写多行数据
         data = [['小玲','25','127567'],['小芳','18','789456'],['小明','20','785656'],['小华','21','475656']]
         writer.writerows(data)   #写多行数据
         print()  #换行符
#    with open('mycsv1.csv', 'r') as fin:
#         cin=csv.reader(fin)        #读csv文件
#         for row in cin:
#             print(row)
    #注意data1的数据格式和data不同
    data1 = [{'姓名':'小玲','年龄':'25','电话':'127567'},{'姓名':'小华','年龄':'20','电话':'577567'},
            {'姓名':'小宝','年龄':'19','电话':'594367'}]
    with open("mycsv1",'wt',newline='') as csvW:
         cw=csv.DictWriter(csvW,fieldnames=['姓名', '年龄', '电话'])
         cw.writeheader()  #写文件头
         cw.writerows(data1)
         csvW.close()    #关闭文件
    with open("mycsv1.csv",'rt') as csvR:
         cr=csv.DictReader(csvR)
         message=[row for row in cr]
         print(message)
     
         
fileOperate()                        
#RegularExpressionOperate()
timeOperate()
#arrayOperate()
#polyOperate()

#stringOperate()
#stringlist() 
#stringtuple()
#stringdict()
#Set()
#structureOperate()
#print(menu("beef","bagal","flan"))
#printinfo(3,24,45,34,22)
#printDict(wine="merlot",entree="mutton",dessert="toast bread")
#print("23+3=",runSomething(add_args,23,3))
#print("5的阶乘为:",runWithPositionalArgs(multply_args,1,2,3,4,5))
#print(knights("No!"))
#EditWords("thud","meow","hiss")
randOperate()



#end =time.clock() #程序结束时间
#print("程序运行了:",end-start) #输出程序运行时间
