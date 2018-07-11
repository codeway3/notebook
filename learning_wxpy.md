# learning wxpy
## 目录结构
```
wxpy  
 |--docs
 |--tests
 |--wxpy
 |	  |--api
 |	  |--compatible
 |	  |--ext
 |	  |--utils
 |	  |--__compat__.py
 |	  |--__init__.py
 |	  |--__main__.py
 |	  |--exceptions.py
 |--.gitignore
 |--LICENSE
 |--MAINIFEST.in
 |--README.rst
 |--requirements.txt
 |--setup.cfg
 |--setup.py	
```  
## explain
MAINIFEST  
mainifest 清单  
无特殊需求不必要 使用setup 走setuptools就可以  
参考 https://stackoverflow.com/questions/24727709/do-python-projects-need-a-manifest-in-and-what-should-be-in-it  
  
setup.cfg  
setup.cfg提供setup.py的默认参数，同时易于修改。Setup.py先解析setup.cfg文件，然后执行相关命令。  
## file analysis
### exceptions
自定义ResponseError异常类，继承自异常基类Exception  
使用super调用父类的__init__构造函数  
### init
`在目录下, 放一个__init__.py文件, 这该目录会被认为包. __init__.py文件, 可以为空. `
`当一个包被import的时候, 会首先加载它的__init__.py文件, 一般可以在__init__.py文件中进行初始化. `
`需要用到包中模块,import的时候使用"."分割. `  
根据导入的包分析代码组织结构，api负责类的抽象定义，utils工具包，ext扩展
### package tests
对接口进行了测试，另外提一点，程序中入口使用了logging进行了日志的记录（虽然还不知道logging怎么用
## PS.
对比当前已获得了3600+个star的wxBot项目（主要逻辑全写在一个文件里，一共有1500行），wxpy真的是很清晰明了

## usage of builtin modules - inspect
reference: [https://docs.python.org/3/library/inspect.html](https://docs.python.org/3/library/inspect.html)  
#### currentframe()
wxpy在handle_response装饰器中使用了inspect的 currentframe()  
`self = inspect.currentframe().f_back.f_locals.get('self')`  
获取解释器栈帧中的信息  
currentframe内部实现是通过sys._getframe实现的。  
#### stack()
在tart_new_thread函数中使用了stack()  
`name = inspect.stack()[1][3]`  
用来获取调用者的名称  
  
至于为什么访问的是[1][3]，参考该[博客](http://blog.csdn.net/heipark_/article/details/49507937)  
#### functools.partial
偏函数 在某个upload函数中使用到了  
作用 减少函数调用中冗余的相同参数 对原函数进行包装 生成附带固定参数的新函数  
  
详情参考[博客](http://blog.csdn.net/handsomekang/article/details/9712125)  
## builtin - weakref
弱引用  
涉及到GC，防内存泄漏？  
wxpy中使用了代理对象的功能，代理对象是弱引用对象，它们的行为就像它们所引用的对象，这就便于你不必首先调用弱引用来访问背后的对象。通过weakref模块的proxy(obj[,callback])函数来创建代理对象。使用代理对象就如同使用对象本身一样
## compatible
```  
import sys as _sys

PY_VERSION = _sys.version
PY2 = PY_VERSION < '3'

if PY2:
    from future.standard_library import print_function
    from future.builtins import str, int  
```  
## comments
函数中使用多行注释，最后使用工具生成文档（我猜
## import usage
\_\_init\_\_.py（即使是空的)，声明当前目录是一个package  
wxpy采用相对引用
`from package import func1, func2, func3 ...`  
同时package下的\_\_init\_\_.py中有一系列的包内导入
`from .module1 import Class`  
`from .module2 import func1, func2 ...`   
而不是的  
`from package.module import func1, func2, func3 ...`  