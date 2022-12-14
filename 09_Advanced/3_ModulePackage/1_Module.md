&emsp;
# Module模块

- 一个包含定义的函数和变量的文件
- 后缀名是 .py
- 模块可以被别的程序引入，以使用该模块中的函数等功能。这也是使用 python 标准库的方法。

>示例
```python
import sys 

for i in sys.argv:
    print(i)

print(sys.path)
```
- import sys 引入 python 标准库中的 sys.py 模块；这是引入某一模块的方法。
- sys.argv 是一个包含命令行参数的列表。
- sys.path 包含了一个 Python 解释器自动查找所需模块的路径的列表。

&emsp;
# 1 import 语句

&emsp;
## 1.1 import `module`
- 导入准备使用的 Python 源文件
>语法
```python
import module1, module2
```
- 当解释器遇到 import 语句，如果模块在当前的搜索路径就会被导入。
- 搜索路径是一个解释器会先进行搜索的所有目录的列表。

>support.py文件代码
```python
def print_func( par ):
    print ("Hello : ", par)
    return
```

>test.py文件代码
```python
import support # test.py 引入 support 模块
support.print_func("AAAA")

# 可以给引入的模块中函数起别名
tt = support.print_func
tt("BBBBB")
```

- 不管你执行了多少次import，一个模块只会被导入一次。这样可以防止导入模块被一遍又一遍地执行。
- Python 中 import 语句的搜索路径，由 sys.path 组成，Python 解释器依次从这些目录中去寻找所引入的模块。这看起来很像环境变量，也可以通过定义环境变量的方式来确定搜索路径。
- 搜索路径是在Python编译或安装的时候确定的，安装新的库应该也会修改。搜索路径被存储在sys模块中的path变量


&emsp;
# 2 from ... import ...语句
## 2.1 from `module` import `classes, functions...`
- 导入某个类或者函数
- 用于普通 .py 文件之间的调用
>示例
```python
from echo import echo_func1
```

&emsp;
## 2.1 from `.module` import `classes, functions...`
- 导入某个类或者函数
- 用在 package 里的 module 之间，且必须这样用
- 如果是普通 py 文件之间的调用，这句会报错
>示例
```py
from .echo import echo_func1
```


&emsp;
# 3 \_\_name__ == \_\_main__ 语句
- 每个模块都有一个 \_\_name__ 属性
- 当其值是'\_\_main__'时，表明该模块自身在运行（即命令：python xx.py），否则是被引入（即 import）

>support.py文件
```python
print("不在__name__ == '__main__'中")

if __name__ == '__main__':
    print("__name__ == '__main__'中执行")
```
>test.py文件
```python
import support
```

- 说明： 
    

&emsp;
# 4 dir() 函数
- 内置的函数 dir() 可以找到模块内定义的所有名称。以一个字符串列表的形式返回
- 如果没有给定参数，那么 dir() 函数会罗列出当前定义的所有名称

>support.py文件
```python
a = [1, 2, 3, 4, 5]

```


>test.py文件
```python
import support

print(dir(support))
print(dir()) # 得到一个当前模块中定义的属性列表
xxx = 5
print(dir()) # 新增了 "xxx"
del xxx
print(dir()) # 删除了 "xxx"
```

