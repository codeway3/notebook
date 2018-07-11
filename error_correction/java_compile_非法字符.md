### 环境：IntelliJ IDEA   
### 报错：Error:(1, 1) java: 非法字符:'\ufeff'  
问题出现在eclipse项目转IDEA项目时，eclipse中会忽略utf-8 with BOM中的BOM签名信息，而IDEA不行，文件头出现乱码。  
尝试改设置中的eclipse编译选项无效。  
### 解决方法 py脚本走起  
代码见github， [这是链接](https://github.com/codeway3/tools/blob/master/BOM_deleter.py)


### 参考资料
[Stack Overflow](https://stackoverflow.com/questions/8898294/convert-utf-8-with-bom-to-utf-8-with-no-bom-in-python)
