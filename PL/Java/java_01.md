## Java “白皮书”的关键术语
* 简单性
* 面向对象
* 网络技能
* 健壮性
* 安全性
* 体系结构中立
* 可移植性
* 解释型
* 高性能
* 多线程
* 动态性

## Java 程序设计环境
* 安装JDK
* 选择开发环境
* 使用命令行工具
* 使用集成开发环境
* 运行图形化应用程序
* 建立并运行 applet

## Java 的基本程序设计结构
#### 一个简单的 Java 应用程序
```Java
public class FirstSample{
  public static void main(String[] args){
    System.out.println("This is the first sample!");
  }
}
```
* 类
Java 程序中的所有内容都包含在类中

* 大小写敏感
Java 对大小写敏感，即区分大小写

* 驼峰命名法
类名以大写字母开头，如果由多个单词组成，每个单词的第一个字母要大写

* 文件名
源代码的文件名必须与公共类的名字相同，并用 .java  作为扩展名

* main 方法
类的源文件中必须包含一个 main 方法，Java 虚拟机将从指定类的 main 方法开始执行

* Java 应用程序的格式
```Java
public class ClassName{
  pubic static void main(String[] args){
    program statements
    }
}
```

#### 注释
* //注释 单行注释

* /\*注释\*/ 多行注释

* /\*\*注释\*/ 可以自动生成文档

#### 数据类型
Java是一种强类型语言。Java 一共有 8 中基本类型，其中有 4 中整型、2 种浮点型、1 种字符型和一种 boolean 类型。
##### 整型
整型用于表示没有小数部分的数值，它允许是负数。Java 提供了 4 种整型，通常情况下，int 类型最常用。

|类型|存储要求|取值范围|
|---|:------:|----|
|int|4 字节|约 -20 亿 ~ 20 亿|
|byte|1 字节| -128 ~ 127|
|short|2 字节| -32768 ~ 32767|
|long|8 字节|约 -$9×10^{18}$ ~ $9×10^{18}$|

* 长整型数值有一个后缀 L，如：4000000000L
* 0xCAFF： 十六进制数
* 010：八进制数（易混淆，不建议使用）
* 0b1001： 二进制数（Java 7 开始支持）

##### 浮点类型
浮点类型用于表示有小数部分的数值。
|类型|存储要求|有效位|
|---|:---:|--|
|float|4 字节|6 ~ 7 位|
|double|8 字节|15 位|

* float 型数值有一个后缀 F
* double 型数值可以有一个后缀 D
* 没有后缀的浮点数默认为 double 类型
* 三个特殊浮点值
  * 正无穷大
  * 负无穷大
  * NaN
    判断 x 是否为NaN的方法：`Double.isNaN(x)`
* 浮点数有舍入误差，精确表示应该使用 BigDecimal 类

##### char 类型
char 类型是用于表示 Unicode 编码的字符单元，其范围从 \\u0000 到 \\uffff。
* 特殊字符的转移序列符

|转移序列|名称|Unicode值|
|:-:|-|:-:|
|\\b|退格|\\u0008|
|\\t|制表|\\u0009|
|\\n|换行|\\u000a|
|\\r|回车|\\u000d|
|\\"|双引号|\\u0022|
|\\'|单引号|\\u0027|
|\\\\ |反斜杠|\\u005c|
* 在 Java 中，char 类型使用 UTF-16 编码表示一个代码单元
* 强烈建议不要使用 char 类型，除非确实需要对 UTF-16 代码单元进行操作

##### boolean 类型
boolean 类型有两个值：false 和 true，用来判断逻辑条件。整型值和布尔值之间不能进行相互转换。

#### 变量
##### 变量命名
Java 中变量名是一个由字母或数字构成的序列
* 必须以字母开头
* 字母包括 'A' ~ 'z'、'a' ~ 'z'、'_'、'$' 或在某种与语言中代表字母的任何 Unicode 字符
* 数字包括 '0' ~ '9' 和某种语言中代表数字的任何 Unicode 字符
* 不能命名为 Java 保留字
* 变量名中的所有字符都是有意义的
* 大小写敏感、长度没有限制
* 检测字符是否属于「字母」的方法：`isJavaIdentifierStart`、`isJavaIdentifierPart`
* '$' 只用于在 Java 编译器或其他工具中生成的名字，不要在自己的代码中使用它

##### 声明
在 Java 中，每一个变量属于一种类型。使用变量前需要先声明变量的类型。
```java
int vacationDays;
double salary;
long earthPopulation;
boolean done;
```
##### 初始化
声明一个变量后，必须用赋值语句对变量进行显示初始化。
* 使用未被初始化的变量，Java编译器会报错
```java
int vacationDays;
System.out.println(vacationDays); //ERROR --variable not initialized
```
* 使用赋值语句初始化变量
```java
int vacationDays;
vacationDays = 12;
```
* 在同一行中声明和初始化变量
```java
int vacationDays = 12;
```

##### 常量
在 Java 中，使用关键字 final 指示常量。常量一旦被赋值，就不能再更改。
```java
final double PAI = 3.14;
```
* 习惯上，常量名使用全大写
* 可以使用 static final 设置一个类常量
  * 类常量的定义位于 main 方法的外部
  * 同一个类的其他方法中也可以使用这个常量
  * 如果一个常量被声明为 public，则 其他类的方法也可以使用这个常量
* const 是 Java 保留的关键字，但目前没有使用。定义常量只能用 final 关键字

#### 运算符
##### 算术运算符
|+|-|*|/|%|
|:-:|:-:|:-:|:-:|:-:|
|加|减|乘|除|取余|
* 用整数除以 0 将会产生一个异常，浮点数除以 0 将会得到无穷大或 NaN
* `x = x + 4` 可以简写作 `x += 4`，其他运算符类推
```java
x = 17 / 2;  // 7
x = 15 % 2;  // 1
x = 15.0 / 2;  // 7.5
x /= 4  //x = x / 4;
```
* 使用关键字 stricp 标记的方法必须使用严格浮点计算

##### 自增运算符和自减运算符
|n++|n--|++n|--n|
|:-:|:-:|:-:|:-:|
|运算再自增|运算再自减|自增再运算|自减再运算|
```java
int m = 7;
int n = 7;
int a = 2 * ++m;  //now a is 16, m is 8
int b = 2 * n++;  //now b is 14, n is 8
```

##### 关系运算符和 boolean 运算符
|==|!=|<|>|<=|>=|
|:-:|:-:|:-:|:-:|:-:|:-:|
|相等|不相等|小于|大于|小于等于|大于等于|

|&&|\|\||!|
|:-:|:-:|:-:|
|与|或|非|
* 计算结果为 true 或 false
* 逻辑运算按照「短路」方式求值
* Java 支持三元操作`?:`
```java
3 == 7;  //false
3 != 7;  //true
x != 0 && 1 / x > x + y;  //由于短路，不会产生除以 0 的错误
min = x < y ? x : y;  //返回 x 和 y 中较小的值
```

##### 位运算符
|&|\||^|~|<<|>>|>>>|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|与|或|异或|非|左移|符号位填充的右移|0 填充的右移|

##### 数学函数与常量
在 Math 类中，包含了各种各样的数学函数。还提供了两个用于表示 π 和 e 常量的近似值
|Math.sqrt|Math.pow|
|:-:|:-:|
|平方根|幂运算|

|常用三角函数|||||
|:-:|:-:|:-:|:-:|:-:|
|Math.sin|Math.cos|Math.tan|Math.atan|Math.atan2|

|指数函数和其反函数|||
|:-:|:-:|:-:|
|Math.exp|Math.log|Math.log10|

|Math.PI|Math.E|
|:-:|:-:|
|π|e|

##### 数值类型之间的转换
* 无损转换
byte → short → int → long
char → int
int → double
float → double

* 有损转换
int → float
long → float
long → double

##### 强制类型转换
使用 `(cast)` 可以强制转换为类型 cast
```java
double x = 9.97;
int nx = (int) x;
```
* 超出目标类型的表示范围的强制转换，结果会被截断
* 不要在 boolean 类型与任何类型之间进行强制转换，需要时可以使用条件表达式 `b ? 1 : 0`

##### 括号与运算符级别
|优先级由上往下递减|
|:-:|
|[] . ()|
|! ~ ++ -- + - () new|
|* / %|
|+ -|
|<< >> >>>|
|< <= > >= instanceof|
|== !=|
|&|
|^|
|\||
|&&|
|\|\||
|?:|
|= += -= *= /= %= &= |= ^= <<= >>= >>>=|

##### 枚举类型
```java
emum Size {SMALL,MEDIUM,LARGE,EXTRE_LARGE};
Size s = Size.MEDIUM;
```

#### 字符串
Java 没有内置的字符串类型，而是在标准 Java 类库中提供了一个预定义类 String。每个用双括号括起来的字符串都是 String 类的一个实例。
```java
String e = "";  //an empty string
String greeting = "Hello";
```
##### 子串
String 类的 `substring` 方法可以从一个较大的字符串中提取出一个子串
```java
String greeting = "Hello";
String s = greeting.substring(0,3);  //now s is "Hel"
```
##### 拼接
Java 语音允许使用 + 号连接两个字符串
```java
String expletive = "Expletive";
String PG13 = "deleted";
String message = expletive + PG13;  //now message is "Expletivedeleted"

int age = 13;
String rating = "PG" + age;  //now rating is "PG13"
```

##### 不可变字符串
String 类中没有提供用于修改字符串的方法。由于不能修改 Java 字符串中的字符，所以在 Java 文档中将 String 类对象称为不可变字符串。
修改字符串要先提取需要的字符，然后再拼接上替换的字符
```java
greeting = greeting.substring(0,3) + "p!";  //now greeting is "Help!"
```

##### 检测字符串是否相等
可以用 `equal` 方法检测字符串是否相等
```java
String greeting = "Hello"
String s = "Help!"
boolean a = s.equals(greeting);  //return false
boolean b = "Hello".equals(greeting);  //return true
```

##### 空串与 Null 值
空串是长度为 0 的串，Null 串是存放了一个 null 值的字符串。
```java
if (str.length() == 0 )
  System.out.println("str 是一个空串");
if (str.equals(""))
  System.out.println("str 是一个空串");
if (str == null)
 System.out.println("str 是一个 Null 串");
if (str != null && str.length() != 0)
  System.out.println("str 既不是空串也不是 null");
```

##### 代码点与代码单元
大多数的常用 Unicode 字符使用一个代码单元就可以表示，而辅助字符需要一对代码单元表示。

`length` 方法获得代码单元数

`codePointCount` 方法获得代码点数，即实际的长度

`charAt` 返回位置为 n 的代码单元

##### API 文档
String 类中包含了 50 多个方法，通过查阅 API 文档可以查阅到所有类的用法

##### 构建字符串
有些时候，需要由较短的字符串构建字符串，如按键或来自文件中的单词。采用字符串连接的方式效率比较低，耗时且浪费空间。
如果需要用许多小段的字符串构建一个字符串，可以先构建一个空的字符串构建器，使用 `append` 方法添加内容，再用 `toString` 方法得到一个 String 对象。
```java
StringBuilder builder = new StringBuilder();
builder.append(ch);  //append a single charater
builder.append(str);  //append a String
String completedString = builder.toString();
```

#### 输入输出
##### 读取输入
想要通过控制台输入，首先需要构建一个 Scanner 对象，并与「标准输入流」 System.in 关联。

`nextLine` 方法读入一行

`next` 方法读取一个单词

`nextInt` 方法读取一个整数

`nextDouble` 方法读取一个浮点数

Scanner 类定义在 java.util 包中，当使用的类不是定义在基本 java.lang 包中时，一定要使用 import 指示字将相应包加载进来
```java
import java.util.*;

/**
  * THis program demonstrates console input.
  * @version 1.10 2004-02-10
  * @author Cay Horstman
*/
public class InputTest
{
  public static void main(String[] args)
  {
    Scanner in = Scanner(System.in);

    //get first input
    System.out.print("What is your name? ");
    String name = in.nextLine();

    //get second input
    System.out.print("How old are you? ");
    int age = in.nextInt();

    //display output on console
    System.out.println("Hello, " + name + ". Next year, you'll be " + (age +1));
  }
}
```
##### 格式化输出
Java SE 5.0 沿用了 C 语言库函数中的 `printf` 方法。
格式说明符：%
```java
double x = 10000.0 / 3
System.out.printf("%8.2f",x);  //3333.33
System.out.printf("Hello, %s. Next year, you'll be %d",ame,age);
System.out.printf("%,.2f",x);  //3,333.2
String message = String.format("Hello, %s. Next year, you'll be %d",ame,age);  //创建一个格式化的字符串而不打印输出
System.out.printf("%tc",new Date()); //打印当前的日期和时间
```

##### 文件输入与输出
要想对文件进行读取，就需要一个用 File 对象构造一个 Scanner 对象。
```java
Scanner in = new Scanner(Paths.get("myfile.txt"));
```
要想写入文件，就需要构造一个 PrintWriter 对象。
```java
PrintWriter out = new PrintWriter("myfile.txt");
```
如果用一个不存在的文件构造一个 Scanner，或者用一个不能创建的文件名构建一个 PrintWriter，那么就会发生异常。因此需要在 main 方法中用 throws 子句标记。
```java
public static void main(String[] args) throw IOException
{
  Scanner in = new Scanner(Paths.get("myfile.txt"));
}
```

#### 控制流程
##### 块控制域
块是指由一对花括号括起来的若干条简单的 Java 语句。
* 块确定了变量的作用域
* 块之间可以相互嵌套，但是不能在嵌套的两个块中声明同名的变量
```java
public static void main(String[] args)
{
  int n;
  ...
  {
    int k;
    int n;  //Error--can't redefine in inner block
    ...
  }// k is only defined up to here
}
```

##### 条件语句
格式： if (condition) statement1 else statement2
* else 部分是可选的。else 子句与最邻近的 if 构成一组
* 重复交替出现 if...else if... 是一种很常见的情况
```java
if (x <= 0) if (x == 0) sign = 0; else sign = 1;
//is equal to :
if (x <= 0) { if (x == 0) sign = 0; else sign = 1; }
```

##### 循环
* while (condition) statement
* do statement while (condition);

##### 确定循环
```java
for (int i = 1; i <= 10; i++)
  System.out.println(i);  //输出1到10
//i no longer defined here

int i;
for (i = 1; i <= 10; i++)
{
  ...
}//i is still defined here
```

##### 多重选择：switch 语句
case标签可以是：
* 类型为 char、byte、short 或 int 的常量表达式
* 枚举常量
* 从 Java SE 7 开始，case 标签可以是字符串字面量
```java
Scanner in = new Scanner(SYstem.in);
System.out.print("Select an option(1,2,3,4) ");
int choice = in.nextInt;
switch (choice)
{
  case 1:
    ...
    break;
  case 2;
    ...
    break;
  case 3;
    ...
    break;
  case 4;
    ...
    break;
  default:
    //bad input
    ...
    break;
}
```

##### 中断控制流程语句
不带标签的 `break` 语句用于退出循环

带标签的 `break` 语句用于跳出到带标签的语句块末尾

`continue` 语句中断正常的控制流程，将控制权转移到最内层循环的首部。

#### 大数值
如果基本的整数和浮点数精度不能够满足需求，那么可以使用 java.math 包中的两个很有用的类：`BigInteger` 和 `BigDecimal`。

`BigInteger` 类实现了任意精度的整数运算

`BigDecimal` 类实现了任意精度的浮点数运算

使用静态的 `valueOf` 方法可以将普通的数值转换为大数值

需要使用大数值类中的 `add` 和 `multiply` 等方法实现算术运算，而不能直接使用算术运算符
```java
BigInteger a = BigInteger.valueOf(100);
BigInteger c = a.add(b);  //c = a + b
BigInteger d = c.multiply.(b.add(BigInteger.valueOf(2)));  //d = c * (b + 2)
```

#### 数组
数组是一种数据结构，用来存储同一类型值的集合。
* 通过一个整型下标可以访问数组中的每一个值，下标从 0 开始
* 声明数组时，需要指出数组的类型和数组变量的名字
* 声明数组变量后，应该用 new 运算符创建数组
* 一旦创建了数组，就不能再改变它的大小
```java
int[] a = new int[100];
for (int i; i<100; i++)
  a[i]=i;  //fills the arrray with numbers 0 to 99
```

##### for each 循环
for each 循环语句的循环变量将会遍历数组中的每个元素，而不需要使用下标值。
```java
for (int element : a)
  System.out.println(elemt);  //打印数组 a 的每一个元素
```

##### 数组初始化以及匿名数组
创建一个数字数组时，所有元素都初始化为 0。boolean 数组的元素会初始化为 false。对象数组的元素则初始化为一个特殊值 null。

在 Java 中，提供了一种创建对象并同时赋予初始值的简化书写方式，这种语句不需要调用 new。

还可以初始化一个匿名的数组，数组的大小就是初始值的个数。使用这种语法格式可以在不创建变量的情况下重新初始化一个数组。
```java
int[] smallPrimes = {2,3,5,7,11,13};
smallPrimes = new int[] {17,19,23,31,37};
```

##### 数组拷贝
Java 中，允许将一个数组变量拷贝给另一个数组变量。这时，两个变量将引用同一个数组。

如果希望将一个数组的所有值拷贝到一个新的数组中去，就要使用 Array 类中的 `copyOf` 方法。

`copyOf` 方法的第二个参数时新数组的长度。这个方法常用来增加数组的大小。
```java
int[] luckyNumbers = smallPrimes;
luckyNumbers[5] = 12;  //now smallPrimes[5] is also 12

int[] copiedLuckyNumbers = Array.copyOf(luckyNumbers,luckyNumbers.length);
luckyNumbers = Array.copyOf(luckyNumbers,2 * luckyNumbers.length);
```

##### 命令行参数
每一个 Java 应用程序都有一个带 String arg[] 参数的 `main` 方法。这个参数表明 `mian` 方法将接收命令行参数，这是一个字符串数组。
```java
public class Massage{
  public static void main(String[] args){
    if (args[0].equal("-h"));
      System.out.print("hello,");
    else if (args[0].equal("-g"))
      System.out.print("Goodbye");
    //print the other command-line arguments
    for (int i; i<args.length; i++)
        System.out.print(" " + arg[i]);
    System.out.print("!");
  }
}
```
对上面代码使用命令 `java Message -g cruel world` 运行程序，args 数组将包含下列内容：
```
args[0]: "-g"
args[1]: "cruel"
args[2]: "world"
```
输出结果为：
```
Goodbye, cruel world!
```

##### 数组排序
想要对数值型数值排序，可以用 Array 类中的 `sort` 方法。

`Math.random` 方法将返回一个 [0,1) 区间的随机浮点数。
```java
int[] numbers = new int[n];
for (int i = 0; i < numbers.length; i++) {
  numbers[i] = i + 1;
}
int[] result = new int[k];
for (int i = 0; i < result.length; i++) {
  int r = (int) (Math.random() * n);
  result[i] = numbers[r];
  numers[r] = numers[n - 1];
  n--;
}
Array.sort(result);
System.out.println("Bet the following combination. It'll make you rich!");
for(int r : result){
  System.out.println(r);
}
```

##### 多维数组
多维数组将使用多个下标访问数组元素，它适用于表示表格或格式更加复杂的排列形式。
```java
double[][] balances;
balances = new double[NYEARS][NRATES];
int[][] mainSquare ={
  {16,3,2,13},
  {5,10,11,8},
  {9,6,7,12},
  {4,15,14,1}
};
for (int j = 0; j < balances[0].length; j++) {
  balances[0][j] = 10000;
}
for (int i = 0; i < balances.length; i++) {
  for (int j = 0; j < balances[i].length; j++) {
    double oldBalances = balances[i - 1][j];
    double interest = ...;
    balances[i][j] = oldBalances + interest;
  }
}
```
for each 循环语句不能自动处理二维数组的每一个元素。要想访问二维数组 a 的所有元素，需要使用两个嵌套的循环
```java
for (double[] row : a)
  for (double value : row)
    do something with value
```
要想快速地打印一个二维数组的数据元素列表，可以调用：
```java
System.out.println(Array.deeToString(a));
```
输出格式为：
```
[[16, 3, 2, 13],[5, 10, 11, 8],[9, 6, 7, 12],[4, 15, 14, 1]]
```

##### 不规则数组
Java 实际上没有多维数组，只有一维数组。多维数组被解释为「数组的数组」。

因此还可以方便地构造一个「不规则」数组，即数组的每一行由不同的长度。不规则数组的行数组需要单独创建。
```java
int[][] odds = new int[MAX + 1][];
for (int n = 0; n <= MAX; n++) {
  odds[n] = new int[n+1];
}
```
