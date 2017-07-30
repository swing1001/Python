# Basic Notes

[TOC]

## (一) 基本数据类型和操作符

- 等式判断用**==** eg: 1 == 1 #True 1==2 #False

- 使用**not**进行取反

- 比较运算可以串联 eg: 1<2<3 #True  2<3<2 #False

- 字符串可以相加 eg: "hello"+"world"="hello world"

- 一个字符串可以看作是一个字符的列表

  > "This is a String"[0] => 'T'

------

- % 可以用来格式化字符串，eg："%s can be %s" % ("strings", "interpolated")

- 后来又有一种格式化字符串的新方法：**format方法**。

  "{0} can be {1}".format("strings", "formatted")

- 如果你不喜欢数数的话，可以使用关键字（变量）。"{name} wants to eat {food}".format(name="Bob", food="lasagna"

------

* **None是一个对象**

> 不要用相等符号"=="来比较对象和None 要有"is"
>
> eg: "etc" is None #False     None is None   #True
>
> *:haha:tips:*
>
> <!--这个'is'比较的是两个对象的标识，对象一旦建立，其标识就不会改变，可以将它认为是对象的内存地址-->

*  None、0 以及空字符串和空列表都等于 False，

   除此以外的所有值都等于 True。0 == False  #=> True   "" == False #=> True

## (二)变量和集合 

1. 在赋值给变量之前不需要声明，变量名的约定是使用下划线分割的小写单词 eg:some_var = 5

   <!--访问为未赋值的变量会产生异常（raise a name error）-->

2. li = [] 列表用于存储序列 

   > other_li = [4, 5, 6]
   >
   > * li.append(1)  => li = [1]  依次append 2,4,3 得到 li = [1, 2, 4, 3]
   >
   > * 通过pop移除最后一个元素li.pop() => li = [1, 2, 4] 再通过append(3)添加=> li = [1, 2, 4, 3]
   >
   > * **像访问数组一样访问列表 ** li[0] = 1
   >
   > * **查询最后一个元素 li[-1]=3**    <!--li[4] raise an IndexError-->
   >
   > * 通过切片来查询列表的一个范围，这个范围是左闭右开区间
   >
   >   <!--li[1:3]=> [2, 4]-->
   >
   >   省略开头li[2:] => [4, 3]  省略结尾li[:3] => [1, 2, 4]
   >
   > * del li[2] 删除列表中任意元素 => li = [1, 2, 3]
   >
   > * 列表相加是进行拼接 li + other_li => [1, 2, 3 , 4, 5, 6]
   >
   > * **通过extend合并列表** li.extend(other_li) => [1, 2, 3, 4, 5, 6]
   >
   > * 用in来检查元素是否存在于某个列表中 eg: 1 in li #True

3. 元组类似于列表，**但不可变**

   * tup = (1, 2, 3)  tup[0] => 1 tup[0]=3 (raise a TypeError ) 不可以给元组赋值
   * 其他操作列表的方式同样适用于元组
   * 可以把元组或列表中的元素解包赋值给多个变量  eg: a, b, c = (1, 2, 3) 
   * **交换两个值 e, d = d, e**

4. 字典用于存储映射关系 empty_dict = {}

   > filled_dict = {"one": 1, "two": 2, "three": 3} 
   >
   > * 通过filled_dict[one] #=>1  键值进行查询
   >
   > * 获取键名和键值列表 filled_dict.keys()  filled)_dict.values()
   >
   >   <!--注意，不能保证输出的键名和键值的顺序，它是无序的-->
   >
   > * 用in来检查一个字典是否包含某个键名 eg: "one" in filled_dict #=> True
   >
   >   * filled_dict["four"] # KeyError          
   >
   >   * 所以要使用 **get 方法来避免键名错误**
   >
   >     filled_dict.get("one") #=> 1filled_dict.get("four") #=> None
   >
   >      get 方法支持传入一个**默认值参数**，将在取不到值时返回。
   >
   >     filled_dict.get("one", 4) #=> 1filled_dict.get("four", 4) #=> 4
   >
   >   * Setdefault方法将新的名值对添加到字典里
   >
   >     filled_dict.setdefault("five", 5) #filled_dict["five"] is set to 5
   >
   >     filled_dict.setdefault("five", 6) #filled_dict["five"] is still 5                        

5. set用来保存集合 empty_set = set()

   * 用一堆值来初始化一个集合 some_set = set([1, 2, 2, 3, 4]) #=>some_set是set([1, 2, 3, 4])

   * 可用{}来声明一个集合 filled_set = {1, 2, 2, 3, 4} #=>{1, 2, 3, 4} 

     <!--集合是种无序不重复的元素集，{}不会创建空的集合，只会创建一个空的列表-->

   * 通过add添加新的元素 filled_set.add(5) #=> {1, 2, 3, 4, 5, 6}

   * 通过&和|取交集和并集，-来取补集

   * 用in检查是否存在某个集合中

## (三)控制流

1. ```python
   some_var = 5
   if some_var > 10:
       print "bigger"
   elif some_var < 10:
       print "smaller"
   else:
       print "equal"
   ```

2. for 循环可以遍历列表

   ```python
   for animal in ["dog", "cat", "mouse"]:
       print "%s is a mammal" % animal
   for i in range(4):
       print i
   ```

3. while循环到条件不满足

   ```python
   x = 0
   while x < 4:
       print x
       x += 1
   ```

4. try/except 来处理代码异常

   ```python
   try：
   	raise IndexError("This is a index error")
   except IndexError as e:
       pass  #(这只是一个空操作，这应该有一些回复操作)
   ```

## (四)函数

1. 用def来创建新函数

   ```python
   def add(x, y):
       print ("x is %s and y is %s") % (x, y)
       return x + y
   # 调用函数并传入参数
   add(5, 6)
   # 传入关键值参数调用函数，参数的顺序可以任意
   add(y=6, x=5)
   ```

2. 可以定义一个函数，让它接受可变数量的定位参数

   ```python
   def varargs(*args):
   	return args
   #调用函数
   varargs(1,2,3) #=>(1, 2, 3)
   ```

3. 也可以定义一个函数，让它接受可变数量的关键值参数

   ```python
   def keyword_args(**kwargs):
       return kwargs
   #调用函数
   keyword_args(bid="foot", loch="ness") #=> {"big": "foot", "loch": "ness"}
   ```

4. 同时使用两类参数

   ```python
   def all_the_args(*args, **kwargs):
   	print args
       print kwargs
   # 调用函数
   all_the_args(1, 2, a=3, b=4)
   # =>(1, 2) {"a":3,"b":4}
   ```

5. 在调用函数时，定位参数和关键值参数还可以反过来用。使用*来展开元组，使用**来展开关键值参数

   ```python
   args = (1, 2, 3, 4)
   kwargs = {"a":3, "b":4}
   all_the_args(*args) #相当于 all_the_args(1, 2, 3, 4)
   all_the_args(**kwargs) #相当于 all_the_args(a=3, b=4)
   all_the_args(*args, **kwargs) # 相当于 all_the_args(1, 2, 3, 4, a=3, b=4)
   ```

6. **闭包：如果在一个内部函数里** ：adder(y)就是这个内部函数

   **对在外部作用域（但不是全局作用域）的变量进行引用** ：x就是被引用的变量，x在外部作用域addx里面，但不在全局作用域里，

   **则这个内部函数adder就是一个闭包**。 

   ```python
   def addx(x):
       def adder(y):
           return x + y
       return adder

   c = addx(10)
   print type(c)  # <type 'function'>
   print c.__name__ # adder
   print c(3) #13
   ```

* 闭包不能修改外部作用域的局部变量

  ```python
  def foo():
      m = 0
      def foo1():
          m = 1
          print m #2
      print m  #1
      foo1()
      print m #3
  foo() 
  #1 0 
  #2 1
  #3 0 闭包中不能修改外部作用域中的局部变量m
  ```

* 一个常用问题：`for i in range (3):print i`  

  **Python的一个问题就是循环结束之后，循环体重的临时变量i不会销毁，而是继续存在于环境中，而且，python函数只有在执行时，才会去找函数体中变量的值。**

  ```python
  flist = []
  for i in range(3): #i = 0,1,2
      def foo(x):
          print x + i
      flist.append(foo)
  print flist
  for f in flist:
      f(2)
  #我们以为的过程是：flist是一个列表，列表中有三个元素，每个元素都是函数foo，第一个函数foo中的i是0，第二个函数foo中的i是1，第三个函数foo中的i是2，所以当执行第二个for循环，依次给foo中的x赋值后，输出的值应该是2，3，4
  # 但实际过程是：当把函数foo加入flist列表中时，并没有给i赋值，只要当执行函数时，才会找i的值，所以相当于list中三个函数中i的值未知，调用时因为第一个for循环结束时，i的值是2，所以三个foo的x值都是2，i的值都是2，所以输出的值是4，4，4
  #修改为：
  for i in range(3):
      def foo(x,y=i):
          print x + y
      flist.append(foo)
  ```

7. 匿名函数：`(lambda x:x>2)(3)` #=> True

8. 內建的高阶函数：

   * `map(c, [1, 2, 3])`  #将函数c作用于给定序列[1, 2, 3]，返回一个列表[11, 12, 13]

   * `filter(lambda x: x > 5, [3, 4, 5, 6, 7])`  #=>[6, 7]

     > `filter(func, seq)` 调用一个bool函数func来迭代遍历每个seq中的元素，返回使func为真的元素的序列

## (五)类

```python
class Human(object):
 
    # A class attribute. It is shared by all instances of this class
    # 下面是一个类属性。它将被这个类的所有实例共享。
    species = "H. sapiens"
 
    # Basic initializer
    # 基本的初始化函数（构造函数）
    def __init__(self, name):
        # Assign the argument to the instance's name attribute
        # 把参数赋值为实例的 name 属性
        self.name = name
 
    # An instance method. All methods take self as the first argument
    # 下面是一个实例方法。所有方法都以 self 作为第一个参数。
    def say(self, msg):
       return "%s: %s" % (self.name, msg)
 
    # A class method is shared among all instances
    # They are called with the calling class as the first argument
    # 类方法会被所有实例共享。
    # 类方法在调用时，会将类本身作为第一个函数传入。
    @classmethod
    def get_species(cls):
        return cls.species
 
    # A static method is called without a class or instance reference
    # 静态方法在调用时，不会传入类或实例的引用。
    @staticmethod
    def grunt():
        return "*grunt*"
    
# Instantiate a class
# 实例化一个类
i = Human(name="Ian")
print i.say("hi")     # prints out "Ian: hi"
                      # 打印出 "Ian: hi"
 
j = Human("Joel")
print j.say("hello")  # prints out "Joel: hello"
                      # 打印出 "Joel: hello"
 
# Call our class method
# 调用我们的类方法
i.get_species() #=> "H. sapiens"
 
# Change the shared attribute
# 修改共享属性
Human.species = "H. neanderthalensis"
i.get_species() #=> "H. neanderthalensis"
j.get_species() #=> "H. neanderthalensis"
 
# Call the static method
# 调用静态方法
Human.grunt() #=> "*grunt*"（六）导入模块

```

## (六)模块

```python
import math 
dir(math) #查出一个模块里有哪些函数和属性
```
