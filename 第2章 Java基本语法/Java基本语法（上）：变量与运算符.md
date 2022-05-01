# Java基本语法（上）：变量与运算符

## 关键字和保留字
关键字：都是小写的  
保留字：现有Java版本尚未使用，但以后版本可能作为关键字，如goto，const  

## 标识符（identifier）
标识符：  
- Java对各种变量、方法和类等要素命名时使用的字符序列称为标识符  
- 技巧：凡事可以自己起名字的地方都叫标识符，比如类名、变量名、方法名、接口名、包名……  

合法标识符规则：  
- 由26个英文字母大小写，0-9，_或$组成
- 数字不可以开头
- 不可以使用关键字和保留字
- Java中严格区分大小写，长度无限制  

标识符的命名规范：  
- 包名：多单词组成时所有字母都小写：xxxyyyzzz
- 类名、接口名：多单词组成时，所有单词的首字母大写：XxxYyyZzz
- 变量名、方法名：多单词组成时，第一个单词首字母小写，第二个单词开始首字母大写：xxxYyyZzz
- 常量名：所有字母都大写，多单词时用_连接：XXX_YYY_ZZZ  

## 变量
1. Java定义变量的格式：数据类型 变量名 = 变量值
2. Java中的每个变量必须先声明、赋值，后使用  

### 变量的数据类型  
- 基本数据类型  
    - 数值型
        - 整数类型 byte, short, int, long
        - 浮点类型 float, double
    - 字符型 char
    - 布尔型 boolean
- 引用数据类型
    - 类 class <- 字符串在这
    - 接口 interface
    - 数组 []  
```java
class Variable{
    public static void main(string[] args){
        // 整型
        // byte(1字节=8bit), 范围-128～127
        byte b1 = 1;
        // short(2字节)
        short s1 = 128;
        // int(4字节=32bit), 最大约21亿
        int i1 = 1234; 
        // long(8字节), 声明long型变量，必须以"l"或"L"结尾
        long l1 = 343434342L;

        // 浮点型
        // float(4字节), double(8字节)
        // ① float, int同为4字节，但float的范围比long还大，因为32bit中有8bit是指数段，
        // ② 通常定义浮点型使用double，精度小数点后14位
        double d1 = 1.3;
        // float型精度小数点后7位，声明float型变量，必须以"f"或"F"结尾
        float f1 = 18.3F;

        // 字符型 char(1字符=2字节), 单引号, 只能保存一个字符, 'ab'不行
        char c1 = 'a'; 
        char c2 = '中';
        char c3 = '\n'; // 转译字符
        char c4 = '\u0043' // Unicode值

        // 布尔型, 取true / false (不是0、1)
        boolean is_bool = true;
    }
}
```

### 基本数据类型之间的运算规则  
前提：这里讨论只是7种基本数据类型变量间的运算，不包括boolean  
1. 自动类型提升  
结论：当容量小的数据类型的变量与容量大的数据类型的变量做运算，结果自动提升为容量大的数据类型  
byte、short、char -> int -> long -> float -> double  
特别的：当byte、short、char三种类型之间做运算时，结果为int型，（byte+byte=int）  
说明：此时的容量大小指的是，表示数的范围的大和小。比如float容量大于long的容量
2. 强制类型转换（自动类型提升运算的逆运算）  
需要使用强转符：()  
强制类型转换，可能导致精度损失
    ```java
    float f = 1.2F;
    int i = (int)f;

    s1 = "123"
    ```  

### 字符串类型：String
1. String是引用数据类型
2. 声明String类型变量时，使用双引号""
3. `String=""`可以，但是`char=''`不行
4. String可以和8种基本数据类型做运算，且只能做连接运算：+ ，运算结果仍然是String类型
```java
class StringTest{
    public static void main(String[] args){
        char c = 'a'; // 97
        int num =  10;
        String str = "hello"; 
        System.out.println(c + num + str); // 107hello
        System.out.println(c + str + num); // ahello10
        System.out.println(c + (num + str)); // a10hello
        System.out.println(str + num + c); // hello10a
    }
}
```

### 不同进制的表示方法
- 二进制binary，以0b或0B开头
- 十进制decimal
- 八进制，以数字0开头
- 十六进制，以0x或0X开头，其中A-F不区分大小写
```java
class BinaryTest{
    public static void main(String[] args){
        int num1 = 0b110;
        int num2 = 110;
        int num3 = 0127;
        int num4 = 0x110A;
    }
}
```

## 运算符
分类
- 算术运算符  
```java
class Test{
    public static void main(String[] args){
        // 除号
        int num1 = 12;
        int num2 = 2;
        int result1 = num1 / num2; // 2
        int result2 = num1 / num2 * num2; // 10
        double result3 = num1 / num2; // 2.0
        double result4 = num1 / (num2 + 0.0); //2.4
        double result5 = (double)num1 / num2; // 2.4

        // 取余 %
        // 结果的符号与被模数的符号相同
        int m1 = 12;
        int n1 = 5;
        System.out.println("m1 % n1 = " + m1 % n1); // 2
        int m2 = -12;
        int n2 = 5;
        System.out.println("m2 % n2 = " + m2 % n2); // -2
        int m3 = 12;
        int n3 = -5;
        System.out.println("m3 % n3 = " + m3 % n3); // 2
        int m4 = -12;
        int n4 = -5;
        System.out.println("m4 % n4 = " + m4 % n4); // -2

        // 前++：先自增后运算
        // 后++：先运算后自增
        int a1 = 10;
        int b1 = ++a1;
        System.out.println("a1 = " + a1 + "b1 = " + b1); // a1=10, b1=11
        int a2 = 10;
        int b2 = a2++;
        System.out.println("a1 = " + a1 + "b1 = " + b1); // a1=10, b1=10
        
        // 注意点：++不会改变本身的数据类型，所以++效率比+1高
        short s1 = 10；
        // s1 = s1 + 1; // 编译失败
        // s1 = (short)(s1 + 1); // 编译正确
        s1 ++; // 11
    }
}
```
- 赋值运算符 =  
+= 不会改变变量本身的数据类型，如
```java
short s1 = 10; 
s1 = s1 + 2; // 编译失败
s1 += 2; // 编译正确
```
- 比较运算符：运算结果是boolean型
- 逻辑运算符  
1. 逻辑运算符只能应用于计算
boolean型  
2. `&`与，`&&`短路与，`|` 或，`||` 短路或，`!` 非，`^` 异或  
3. 区分`&`与`&&`：当符号左边为false时，`&&`不执行右边部分  
4. 区分`|`与`||`：当符号左边为true时，`||`不执行右边部分  
- 位运算符
1. 位运算符操作的都是整型的数据  
2. `<<`左移，`>>`右移，`>>>`无符号右移（没有`<<<`），`&`与，`|`或，`^`异或，`~`取反  
3. `>>>`无符号右移，被移位二进制最高位无论是0或者1，空缺位都用0补；而`>>`最高位为0用0补，为1用1补
- 三元运算符  
(条件表达式)?表达式1:表达式2  
三元运算符一般来说比if-else效率更高

