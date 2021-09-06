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
 
