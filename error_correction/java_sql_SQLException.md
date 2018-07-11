### 问题原因  
  
用户对应的密码不正确  
  
当主机填写为localhost时mysql会采用 unix domain socket连接  
当主机填写为127.0.0.1时mysql会采用 tcp方式连接  
  
这是linux套接字网络的特性，win平台不会有这个问题  
   
### 解决方法  
在my.cnf的[mysql]区段里添加  
代码如下	
protocol=tcp
