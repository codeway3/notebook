## range vs xrange  
```
在python3中，xrange的功能与range进行了合并。  
所以在python3中没有xrange这个方法，  
而且与python2不同的是，range()类型为'range'，  
```  
故以下讨论基于python2  
usage:  

```
range([start,]stop[,step])
```  
根据起点，终点，和步长生成一个序列  
example:  

```
In:range(5)  
Out:[0,1,2,3,4]  
In:range(1,5)  
Out:[1,2,3,4]  
In:range(0,6,2)  
Out:[0,2,4]  
```  
xrange用法与range完全相同，但是range生成一个列表，xrange是一个生成器。  
主要用处是用来循环，因为xrange是生成器，所以性能更好，除非要求返回值为列表，否则建议都使用xrange。  