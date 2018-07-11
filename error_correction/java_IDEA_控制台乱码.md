### 问题：IDEA控制台输出中文会显示为“?”  
  
### 解决方法：  
在Tomcat配置的VMoption里加一句  
-Dfile.encoding=utf-8  
  
注：在当前新版本IDEA（2017.2）中有效。
