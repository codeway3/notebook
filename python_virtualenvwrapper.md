## virtualenvwrapper与项目绑定  
### 创建虚拟环境时  
```
mkvirtualenv [-a project_path] [-i package] [-r requirements_file] [virtualenv options] ENVNAME
```
-a 将一个虚拟环境与一个项目绑定，每次workon 虚拟环境，直接进入工程目录，在工程目录下工作  
### 创建虚拟环境后  
```
setvirtualenvproject [virtualenv_path project_path]
```  
将一个已经存在的虚拟环境和已经存在的工程绑定，每次workon ENVNAME 直接使用python虚拟环境在绑定项目目录下工作  
## 激活虚拟环境 进入项目目录  
### 激活同时进入
```
workon my_project -c
```  
### 激活后进入
```
cdproject
```  