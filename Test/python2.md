# python杂类

## 1. 装饰器

### 1.1 @property

>当你在一个方法前面使用 `@property` 装饰器时，它将这个方法转变为一个只读属性。
>
>这意味着你可以像访问属性一样访问这个方法，而不需要使用括号进行函数调用。

```python
class MyClass:
  @property
  def test_1(self):
    return 22
 
obj = MyClass()
value = obj.test_1 
print(value) # --->22
```



## 2. 模块

### 2.1 six

Python 2.x中的`six`模块，该模块提供了一些与兼容Python 2和Python 3版本相关的辅助函数和类型

```python
if not isinstance(value, six.string_types):
	raise ValueError("the format of input argument{} is not string".format(value))
```

python3的等效代码

```python
if not isinstance(value, str):
    raise ValueError("the format of input argument {} is not a string".format(value))
```

