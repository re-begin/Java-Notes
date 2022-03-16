# Java语言概述

## 基础知识
- JDK、JRE、JVM关系：  
    JDK = JRE + 开发工具集（例如Javac编译工具等）  
    JRE = JVM + Java  

- Java程序编写-编译-运行的过程
    1. 编写：写.Java文件
    2. 编译：通过javac.exe对java文件进行编译，得到.class文件（也称字节码文件）
    3. 运行：通过java.exe对生成的.class文件运行   

- Windows不区分大小写，Java区分大小写  

- 一个Java源文件中可以声明多个class，但最多只能有一个类声明为public，且要求声明为public的类的类名必须与源文件名相同  

- javac.exe编译以后，会生成一个或多个.class文件，文件名和类名一致，多个类生成多个.class文件

## Hello world
```java
class helloworld{
    public static void main (String[] args){
        System.out.println("Hello, world!");
    }
}
```

## 注释
- 单行注释
    ``` java
    //单行注释
    ```
- 多行注释
    ``` java
    /*多
      行
      注
      释
    */
    ```
- 文档注释（多用于注释文件或函数）
    ``` java
    /**
        @author xxx
        @version xxx
        xxx
    */
    ```
    文档注释可被JDK提供的工具javadoc所解析，生成一套以网页文件形式体现的该程序说明文档  

    操作方式（命令行中输入如下命令） 
    ```
    javadoc -d '文件夹名' -author -version '文件名.java'
    ```