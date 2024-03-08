python入门篇

环境

>windows
>
>1. 下载安装包: https://www.python.org/downloads/
>2. 默认一键安装
>3. 配置环境变量
>   - 【右键计算机】-->【属性】-->【高级系统设置】-->【高级】-->【环境变量】
>   - 【在第二个内容框中找到 变量名为Path 的一行，双击】 -->【Python安装目录追加到变值值中，用 ; 分割】
>
>Mac、Linux 自带python, 也可以更新就不赘述了
>
>检查: 打开终端输入命令 -->`python --version`





>- 手动格式字符串
>  - 字符串拼接繁琐不够灵活
>
>
>```python
># 坏习惯
>name = '李华'
>say_hi = '我' + name + '没考上大学'
>
># 好习惯
>name = '李华'
>say_hi = f'我{name},没考上大学'
>say_hello = '我{},没考上大学'.format(name)
>
>```
>
>- 手动关闭文件
>  - 步骤麻烦容易忘记
>  - 使用with语句，发生异常更加安全可靠
>
>```python
># 坏习惯
>file = open('test.txt', 'r')
>content = file.read()
>file.close()
>
># 好习惯
>with open('test.txt', 'r') as file:
>  content = file.read()
>```
>
>- 裸用except
>  - 裸用会捕捉所有异常，看不到真正的错误
>
>```python
># 坏习惯
>try:
>  res = 10 / 0
>except:
>  print('error')
>  
># 好习惯
>try:
>  res = 10/ 0
>except ZeroDivisionError:
>  print('error')
>```
>
>- 默认参数可变
>  - 默认参数是指函数被定义时被计算，而不是在每次函数调用时
>  - 如果是可变在调用之间会出现错误
>
>```python
># 坏习惯
>def add_item(item, items=[]):
>  return items.append(item)
>
># 好习惯
>def add_item(item, items=None):
>  return items.append(item)
>```
>
>- 不会用推导式子
>  - 是一种python的语法糖，可以减少代码行数跟链式编程一样
>
>```python
># 坏习惯
>arr = []
>for i in rang(5):
>  arr.append(i ** 2)
>  
># 好习惯
>arr = [i ** 2 for i in rang(5)]
>```
>
>- 使用type(x)检查类型
>  - type不如isinstance灵活，且无法处理继承关系
>
>```python
># 坏习惯
>value = 2
>if type(value) is int:
>  return True
>
># 好习惯
>value = 2
>if isinstance(value, int):
>  return True
>```
>
>- 使用 =\= 判断是否为None True 或 False
>  - 在python中，None、True、False是单例对象，使用`is`比较的是对象的身份。
>  - 对象的\__eq\_\_方法可以被重载，=\=不能进行全部场景的比较
>
>```python
># 坏习惯
>if x == None:
>  print('x is None')
>  
># 好习惯
>if x is None:
>  print('x is None')
>```
>
>- 使用bool(..) 或 len(..)进行条件检查
>  - 在条件判断时使用可读性更高的表达式，不必显示地检查长度或者真值
>
>```python
># 坏习惯
>list = [1,2,3]
>if len(list) != 0:
>  return True
>
># 好习惯
>list = [1,2,3]
>if list:
>  return True
>```
>
>
>
>```python
>```
>
>
>
>```python
>
>```
>
>
>
>
>
>
>
>











​	💻**python编程习惯分享**💻

​	📌==每天多巩固一招==📌

​	📎Look L22k📎

