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
MAINIFEST.in  
mainifest 清单  
无特殊需求不必要 使用setup.py 走setuptools就可以  
参考 https://stackoverflow.com/questions/24727709/do-python-projects-need-a-manifest-in-and-what-should-be-in-it  
  
setup.cfg  
setup.cfg提供setup.py的默认参数，同时易于修改。Setup.py先解析setup.cfg文件，然后执行相关命令。  
## file analysis
### exceptions.py
自定义ResponseError异常类，继承自异常基类Exception  
使用super调用父类的__init__构造函数  
### init.py
`在目录下, 放一个__init__.py文件, 这该目录会被认为包. __init__.py文件, 可以为空. `
`当一个包被import的时候, 会首先加载它的__init__.py文件, 一般可以在__init__.py文件中进行初始化. `
`需要用到包中模块,import的时候使用"."分割. `  
根据导入的包分析代码组织结构，api负责类的抽象定义，utils工具包，ext扩展
### package tests
对接口进行了测试，另外提一点，程序中入口使用了logging进行了日志的记录（虽然还不知道logging怎么用
## PS.
对比当前已获得了3600+个star的wxBot项目（主要逻辑全写在一个文件里，一共有1500行），wxpy真的是很清晰明了