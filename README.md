# python简单小例子
## 面向对象编程基础
### 类的定义
***
通过class关键字来对类进行定义，可以在类中定义属性（即变量）和方法（即函数）
```python
class print_name1:
	def __init__(self,name):
	#__init__是创建对象时进行初始化操作的特殊方法
		self.name = name
	def putOut(self):
		print('您的名字是：%s'%self.name)
#由于__init__的属性原因，在这里对于类的调用时，必须要传入name的值
 a=print_name1('hcq')
 a.putOut()
 #不传入name的值程序会直接报错，错误类型：TypeError
 ```
 在此如果不使用此函数，而是通过定义普通的函数传入name值，如
 ```python
	def SetName(self,name):
	 self.name = name
```
此时对类的调用可不传入参数，即可得到相同的结果
```python
 a=print_name1()
 a.SetName('hcq')
 a.putOut()
 ```
 ### 公有和私有
***
在python中，对于类中的属性一般来说都是公有的（Public），如果希望定义一个私有的属性，则需要在属性的命名前加上两个下划线作为标识，这样定义出的属性就是私有的(Private)。

### 类的继承
***
继承的概念是一种类与类的关系，在定义了一个父类之后，通过继承的方法可以继承父类的属性和方法，Python有单继承与多继承。这里通过一个小例子来进行演示。
```python
import random as r
#这里通过import方法来导入random模块
class fish:
    def __init__(self):
        self.x=r.randint(0,10)
        self.y=r.randint(0,10)
    def move(self):
        self.x-=1
        print('我的位置是',self.x,self.y)
class goldfish(fish):
    pass
class crap(fish):
    pass
class salmon(fish):
    pass
class shark(fish):
    def __init__(self):
        super().__init__()
        #此时子类对__init__方法进行了重写，如还需要继承父类的方法，需使用super函数
        self.hungry=True

    def shark_eat(self):
        if self.hungry:
            self.hungry=False
            print('吃饱了')
        else:
            print('吃不下了')
```
上一个例子进行了单继承的演示，除此之外，python支持多继承，即一个子类可以继承多个父类，但多继承的不同的父类之间的方法可能产生冲突，所以还是要谨慎使用
```python
class parent1:
    def fun1(self):
        print('正在调用fun1')
class parent2:
    def fun2(self):
        print('正在调用fun2')
class parent3:
    def fun3(self):
        print('正在调用fun3')
class child(parent1,parent2,parent3):
    pass
 ```
### 类相关的BIF（内置函数）
***
1\.`issubclass(class,classinfo)`
函数用于判断一个类是否为另一个类的子类，classinfo可以是一个由类组成的元组，若class属于元组中任意一个类的子类，则返回True
2\.`hasattr(object,name)`
函数用于判断属性是否在对象中，object传入对象名，name传入属性名，需要注意传入属性名时必须以字符串的形式传入，否则会报错。
3\.`getattr(object,name[,default])`
函数用于返回对象指定的属性值，如果指定的属性不存在，函数会打印default参数，若default参数也不存在，会报AttributeError的错误
4\.`setattr(object,name,value)`
函数用于在object对象中的name属性进行value的赋值，若name属性不存在，会定义一个新的name属性
5\.`delattr(object,name)`
函数用于删除object对象中的name属性，若属性不存在，会直接报错
### 魔法方法
***
