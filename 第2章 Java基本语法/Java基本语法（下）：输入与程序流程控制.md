# Java基本语法（下）：输入与程序流程控制
## 输入  
如何从键盘获取不同类型的变量：需要使用Scanner类  
具体实现步骤：  
1、导包：import java.util.Scanner;  
2、Scanner的实例化: Scanner scan = new Scanner(System.in)  
3、调用Scanner类的相关方法，来获取指定类型的变量  
```java
import java.util.Scanner;

class ScannerTest{
    public static void main(String[] args){
        Scanner scan = new Scanner(System.in);
        
        int num = scan.nextInt();
        System.out.println(num);

        String str = scan.next();
        double num2 = scan.nextDouble();
        boolean isTrue = scan.nextBoolean();

        // 对于Char型的获取，Scanner没有提供相关方法，只能获取字符串
        String str2 = scan.next();
        char chr = str2.charAt(0); // 获取索引为0的字符
    }
}
```

## 顺序结构
程序从上到下逐行的执行，中间没有任何判断和跳转
## 分支结构
根据条件，选择性的执行某段代码  
有`if-else`和`switch-case`两种分支语句  
```java
// 格式1
if(条件){
    执行语句;
}
// 格式2
if(条件){
    执行语句;
}else{
    执行语句;
}
// 格式3
if(条件){
    执行语句;
}else if(条件){
    执行语句;
}else{
    执行语句;
}
```
```java
/* 
1、一定要加break，否则后续内容全部输出
2、switch中的表达式，只能是如下的6种数据类型之一：
    byte、short、char、int、枚举类型(JDK5.0新增)、String(JDK7.0新增)
3、case之后只能声明常量，不能声明范围如: case num > 1
4、default是可选的，而且位置是灵活的
*/
switch(表达式){
case 常量1:
    执行语句1;
    break;
case 常量2:
    执行语句2;
    break;
default:
    执行语句n;
}
```
## 循环结构
根据循环条件，重复性的执行某段代码 
有`for`, `while`, `do...while`三种循环语句  
注：JDK1.5提供了`foreach`循环，方便的遍历集合、数组元素  
循环结构的四个要素:  
① 初始化条件  
② 循环条件：是boolean类型  
③ 循环体  
④ 迭代条件  
```java
for(①; ②; ④){
    ③
}

// 示例，输出结果为：abcbcbc
int num = 1;
for(System.out.print('a'); num <=3; System.out.print('c'),num++){
    System.out.print('b');
}
```
```java
① 
while(②){
    ③;
    ④; // 切记不要忘记写迭代条件，否则易出现死循环
}
```
```java
① 
do{
    ③;
    ④; 
}while(②);
```
```java
/* 
例题：输出100以内的所有质数
*/
class PrimeNumberTest{
    public static void main(String[] args){

        boolean isFlag = true; // 标记i是否被j除尽，一旦除尽，修改为false
        for(int i = 2; i <= 100; i++){
            for(int j = 2; j <= Math.sqrt(i); j++){ // 优化：Math.sqrt(i)
                if(i % j == 0){ 
                    isFlag = false;
                    break; // 优化：一旦被除尽就可以跳出循环了
                }
            }
            if(isFlag){
                System.out.println(i);
            }
            isFlag = true;
        }
    }
}
```
