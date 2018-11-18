# python class 
## python staticmethod
静态方法和一般的函数十分相似，都不可访问class内部的变量和init里头的实例变量

  
## python classmethod
类方法把一个类作为第一个接受的函数值，可以访问class内部的变量但不能访问实例变量

普通方法(simple)类方法(classmethod)静态方法(staticmethod)的区别只需要抓住这一点他们都写在class类内.``` 
class A(object):  
def f(self, x):
  pass  
@classmethod  
def f(cls, x): 
  pass 
@staticmethod 
def f(x): 
  passa = A()
```
所以他们唯一的区别是函数的第一个参数绑定的对象不一样:普通方法(simple) def f(self, x): 的第一个参数 self 绑定的对象是实例对象 a, 第二个参数是 x ;类方法(classmethod) def f(cls, x): 的第一个参数 cls 绑定的对象是类 A , 第二个参数是 x ;静态方法(staticmethod) def f(x): 的第一个参数就是传参 x 自己.
