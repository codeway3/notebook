Java的变量作用域一共有四种，分别是类级、对象实例级、方法级、块级。  
* 类级变量又称全局级变量或静态变量，需要使用static关键字修饰，类级变量在类定义后就已经存在，占用内存空间，可以通过类名来访问，不需要实例化。  
* 对象实例级变量就是成员变量，实例化后才会分配内存空间，才能访问。  
* 方法级变量就是在方法内部定义的变量。  
* 块级变量就是定义在一个块内部的变量，变量的生存周期就是这个块，出了这个块就消失了，比如 if、for 语句的块，还有static块。  
```Java
public class demo
{
    public static String name = "hello";//类级变量
    public int i;//对象级变量，默认为0
    static{
        int j = 1;//块级变量，只能在块内部访问
    }
    public void test()
    {
        int k = 2;//方法级变量，只能在该方法内使用
        System.out.println("i=" + i);
    }
    public static void main(String[] args)
    {
        System.out.println("name");//类级变量不需要实例化对象就可使用
        demo d = new demo();
        d.test();
    }
}
```