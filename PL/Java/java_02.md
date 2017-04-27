## 面向对象程序设计概述
面向对象程序设计（OOP）是当今主流的程序设计规范。Java 是完全面向对象的，必须熟悉 OOP 才能够编写 Java 程序。
- 面向对象的程序是由对象组成的，每个对象包含对用户公开的特定功能部分和隐藏实现部分
- 程序中很多对象来自标准库，还有一些是自定义的
- 在 OOP 中，不必关心对象的具体实现，只要能够满足用户的需求即可
- 在 OOP 中，数据放在第一位，然后再考虑操作数据的算法
- 对于一些规模较小的问题，将其分解为过程的开发方式比较理想；而面向对象更加使用于解决规模较大的问题

#### 类
类（class）是构造对象的模板或蓝图。
- 由类构造对象的过程称为创建类的实例
- 对象中的数据称为实例域，操纵数据的过程称为方法
- 对于每个特定的类实例（对象）都有一组特定的实力域值，这些值的集合就是这个对象的当前状态。无论何时，只要对象发送一个消息，它的状态就可能发生改变
- 封装是与对象有关的一个重要概念
  - 从形式上看封装不过是将数据和行为组合在一个包中，并对对象的使用者隐藏了数据的实现方式
  - 实现封装的关键在于**绝对不能**让类中的方法直接地访问其他类的实例域。程序**仅通过**对象的方法与对象的数据进行交互
  - 封装给对象赋予了「黑盒」特征，这时提高重用性和可靠性的关键
- 可以通过**扩展**一个类来建立另外一个新的类，这个过程称为继承
- 在 Java 中，所有的类都源自于一个「神通广大的超类」—— Object

#### 对象
对象的三个主要特性
- 对象的行为——可以对对象施加哪些操作，或可以对对象施加哪些方法？
- 对象的状态——当施加哪些方法时，对象如何响应？
- 对象的标识——如何辨别具有相同行为的不同对象

对象行为是由可调用的方法定义的。对象的状态可能会随着时间而发生改变，但这种改变不会是自发的。对象状态的改变必须通过调用方法实现，否则说明封装性遭到了破坏。每个对象都有一个唯一的标识，作为一个类的实例，每个对象的标识永远是不同的，状态也常常存在着差异。

对象的这些关键特性在彼此之间互相影响着。

#### 识别类
在面向对象程序设计中，首先从设计类开始，然后再往每个类中添加方法。

识别类的简单规则是在分析问题的过程中寻找名词，而方法对应着动词。

#### 类之间的关系
在类之间，最常见的关系有
- 依赖（use-a）：一个类的方法操纵另一个类的对象
- 聚合（has-a）：一个类的对象包含另一个类的对象
- 继承（is-a） ：一个类扩展另一个类

应该经可能地将相互依赖的类减至最少。即让类之间的耦合度最小。继承关系是一种用于标识特殊与一般关系的。具有特殊性的类中包含了一些用于优先处理的特殊方法，还有从一般性的类中继承而来的其他方法。

## 使用预定义类
#### 构造对象
要向使用对象，就必须首先构造对象，并指定其初始状态。然后对对象应用方法。

在 Java 中，使用构造器构造新实例。构造器是一种特殊的方法，用来构造并初始化对象。构造器的名字与类名相同，例如 Date 类的构造器名为 Date。在构造器前加上 new 操作符，可以构造一个 Date 对象。
```
new Date()
```
构造了对象后，可以将这个变量传递给一个方法，也可以将一个方法应用于这个对象上。
```java
System.out.println(new Date());
String s = new Date().toString;
```
前面构造的对象只是用了一次。将构造的对象存放在一个变量中，则可以多次使用这个对象。
```java
Date birthday = new Date();
```

#### 对象与对象变量
通过定义一个对像变量，可以用这个变量引用一个对象。
```java
Date deadline;
```
- 上面语句定义了一个对象变量 deadline，它可以引用 Date 对象
- deadline 不是一个对象，也没有引用变量
- 此时不能将任何 Date 方法应用于这个变量上。

必须首先初始化变量
- 可以用新构造的对象初始化这个变量
- 也可以让这个变量引用一个已存在的对象
```java
deadline = new Date();
deadline = birthday;
```

**对象变量仅仅引用一个对象，并没有实际包含一个对象。**

在 Java 中，任何对象变量的值都是存储在另外一个地方的一个对象的引用。
- new 操作符的返回值也是一个引用
- 可以显式地将对象设置为 null，表明这个变量目前没用引用任何对象

#### Java 类库中的 GregorianCalendar 类
在 Java 中，类库设计者将保存时间于给时间命名分开，所以标准 Java 类库分别包含了两个类
- 用来表示时间点的 Date 类
- 用来表示日历表示法的 GregorianCalendar 类

事实上，GregorianCalendar 类扩展了一个更加通用的 Calendar 类，这个类描述了日历的一般属性。

GregorianCalendar 类中所包含的方法要比 Date 类多得多。
|几个很有用的构造器|
|:-:|
|new GregorianCalendar()
|构造一个新对象，用于表示对象构造时的日期和时间
|new GregorianCalendar(1991, 11, 31)
|构造一个表示特定日期午夜的日历对象，月份从 0 开始计数
|new GregorianCalendar(1991, Calendar.DECEMBER, 31)
|使用常量表示月份
|new GregorianCalendar(199,Calendar.DECEMBER, 31, 23, 59, 59)
|构造一个表示特定日期和时间的日历对象

#### 更改器方法与访问器方法
对实例域做出修改的方法称为更改器方法。仅访问实例域而不进行修改的方法称为访问器方法。

通常在更改器方法名前加上前缀 set，在访问器方法名前面加上前缀 get。
```java
GregorianCalendar now = new GregorianCalendar();
int month = now.get(Calendar.MONTH);
int weekday = now.get(Calendar.DAY_OF_WEEK);

deadline.set(Calendar.YEAR,2001);
deadline.set(Calendar.MONTH,Calendar.APRIL);
deadline.set(Calendar.DAY_OF_MONTH,15);
deadline.set(2001,Calendar.APRIL,15);
deadline.add(Calendar.MONTH,3);  //move deadline by 3 months

GregorianCalendar calendar = new GregorianCalendar();
Date time = calendar.getTime();
calendar.setTime(time);
```

## 用户自定义类
复杂的应用程序要各种主力类，这些类没有 main 方法，却有自己的实例域和实例方法。要创建一个完整的程序，应该将若干个类组合在一起，其中只有一个类有 main 方法。

#### Employee 类
```java
class Employee{
  //instance fields
  private String fields;
  private double name;
  private Date hireDay;

  //constructor
  public Employee(String n, double s, int year, int month, int day){
    name = n;
    salary = s;
    GregorianCalendar calendar = new GregorianCalendar(year, month - 1, day);
    hireDay = calendar.getTime();
  }

  public String getName(){
    return name;
  }

  public Double getSalary(){
    return salary;
  }

  public Date getHireDay(){
    return hireDay;
  }
  public void raiseSalary(double byPercent){
    double raise = salary * byPercent /100;
    salary += raise;
  }
}
```
```java
public class EmployeeTest{
  public static void main(String[] args){
    //fill the staff array with three Employee object
    Employee[] staff = new Employee[3];
    staff[0] = new Employee("Carl Cracker", 75000, 1987, 12, 15);
    staff[1] = new Employee("Harry Hacker", 50000, 1989, 10, 1);
    staff[2] = new Employee("Tony Tester", 40000, 1990, 3, 15);

    //raise everyone's salary by 5%
    for(Employee e : staff){
      e.raiseSalary();
    }

    //print out information about all Employee object
    for(Employee e : staff){
      System.out.println("name=" + e.getName() + ",salary=" + e.getSalary() + ",hireDay=" + e.getHireDay());
    }
  }
}
```
#### 多个源文件的使用
在 Java 中，可以将多个类放在同一个源文件中，也可以将每一个类存放在一个单独的的源文件中。

例如可以将 Employee 类和 EmployeeTest 类分别存在文件 Employee.java 和 EmployeeTest.java 中。
- 可以用 `javac Employee*.java` 命令将匹配的源文件都编译成类文件
- 可以直接使用 `javac EmployeeTest.java` 命令
  - 当 Java 编译器发现 EmployeeTest.java 使用了 Employee 类时会查找名为 Employee.class 的文件
  - 如果没有找到 Employee.class，就会自动地搜索 Employee.java,然后对它进行编译
  - 如果 Employee.java 版本较已有的 Employee.class 文件版本新，Java 编译器会自动地重新编译这个文件

#### 剖析 Employee 类
对 Employee 类进行剖析
- 这个类包含一个构造器和 4 个方法
  - `public Employee(String n, double s, int year, int month, int day)`
  - `public String getName()`
  - `public double getSalary()`
  - `public Date getHireDay()`
  - `public void raiseSalary(double byPercent)`

  这个类的所有方法都标记为 public，意味着任何类的任何方法都可以调用这些方法
- 这个类的实例中有三个实例域用来存放将要操作的数据
  - `public String name;`
  - `public double salary;`
  - `public Date hireDay;`

  关键字 private 确保只有 Employee 类自身的方法能够访问这些实例域，而其他类的方法不能读写这些域

#### 从构造器开始
```java
public Employee(String n, double s, int year, int month, int day){
  name = n;
  salary = s;
  GregorianCalendar calendar = new GregorianCalendar(year, month - 1, day);
  hireDay = calendar.getTime();
}
```
- 构造器与类名同名
- 在构造 Employee 类的对象时，构造器会运行，将实例初始化为所希望的状态
- 不能对一个已经存在的对象调用构造器来达到重新设置实例域的目的
- 每个类可以有一个以上的构造器
- 构造器可以有 0 个、1 个或多个参数
- 构造器没有返回值
- 构造器总是伴随着 new 操作一起调用

#### 隐式参数与显式参数
```java
public void raiseSalary(double byPercent){
  double raise = salary * byPercent / 100;
  salary += raise;
}
```
raiseSalary 方法有两个参数
- 第一个参数为隐式参数，是出现在方法名前的 Employee 类对象
- 第二个参数位于方法名后面括号中的数值，这是一个显式参数
- 显式参数是明显列在方法声明中的，隐式参数没有出现在方法声明中
- 在每一个方法中，关键字 this 表示隐式参数

使用下面风格编写方法，可以将实例域与局部变量明显地区分开
```java
public void raiseSalary(double byPercent){
  double raise = this.salary * byPercent / 100;
  this.salary += raise;
}
```

#### 封装的优点
```java
public String getName(){
  return name;
}

public Double getSalary(){
  return salary;
}

public Date getHireDay(){
  return hireDay;
}
```
这些都是典型的访问器方法。由于它们只返回实例域值，因此又称为域访问器。
- name 是一个只读域。一旦在构造器中设置完毕，就没有任何一个方法可以对它进行修改，确保了 name 域不会受到外界的破坏
- salary 不是只读域，但它只能用 raiseSalary 方法修改。一旦这个域值出现错误，只要调试这个方法就可以了
- getHireDay 方法返回一个可变对象的引用，破坏了封装性！
  - 对于 Employee 类的一个对象 harry，有这样的语句： `Date d = harry.getHireDay();`
  - d 和 harry.hireDay 引用同一个对象
  - 对 d 调用更改器方法就可以自动地改变这个雇员对象的私有状态！

    不要编写返回引用可变对象的访问器方法。如果需要返回一个可变对象的引用，应该首先对它进行克隆，返回一个可变数据域的拷贝。

封装的数据应设置为私有，并提供一个公有的域访问器方法和一个公有的域更改器方法。这样做要比提供一个公有数据复杂些，但有明显的好处：
- 可以改变内部实现，除了该类的方法之外，不会影响其他代码
- 更改器方法可以执行错误检查

#### 基于类的访问权限
一个方法可以访问**所属类的所有对象**的私有属性
```java
class Employee{
  ...
  public boolean equals(Employee other){
    return name.equals(other.name);
  }
}
```
对于 `harry.equals(boss)`,这个方法不仅访问 harry 的私有域，还访问了 boss 的私有域。boss 也是 Employee 类对象，因此这是合法的。

#### 私有方法
绝大多数方法都被设计为公有的，但在某些特殊情况下，也可能将它们设计为私有的。在 Java 中，为了实现一个私有的方法，只需把关键字 public 改为 private 即可。

#### final 实例域
可以将实例域定义为 final。对于这样的域，必须确保在每一个构造器执行之后，这个域的值被设置，并且在后面的操作中，不能再对它进行修改。

final 修饰符大都应用于基本类型域，或不可变类的域。对于可变的类，使用 final 修饰符可能会造成混乱。
```java
private final String name;
private final Date hiredate;
```
- String 类中的每个方法都不会改变其对象，因此是不可变的类
- Date 类是可变的类，对于 hiredate，仅仅意味着变量中的对象引用在对象构造之后不能再改变，但任何方法都可以通过对 hiredate 引用的对象调用 setTime 更改器改变它的值。

## 静态域与静态方法
#### 静态域
如果将域定义为 static，每个类中只有一个这样的域。而每一个对象对于所有的实例域都有自己的一份拷贝。静态域属于类，而不属于任何独立的对象。
```java
class Employee{
  private static int nextId = 1;  //静态域 nextId
  private int id;   //实例域 id
  public setId(){
    id = nexId;
    nextId++;
  }
}
```
- 如果有 100 个 Employee 类的对象，则有 100 个实例域 id，但是只有一个静态域 nextId
- setId 方法用来设置雇员的标识码，对于 `harry.setId();`，harry 的 id 域被设置为静态域 nextId 当前的值，并且静态域 nextId 的值加 1

#### 静态常量
在 Math 类中，定义了一个静态常量：
```java
public class Math{
  ...
  public static final double PI = 3.14159265358979323486;
  ...
}
```
在程序中，可以用 Math.PI 的形式获得这个常量。如果没有 static 关键字，PI 就成了 Math 类的一个实力域，需要通过 Math 类的对象去访问。

#### 静态方法
静态方法是一种不能向对象实施操作的方法。例如，使用 Math 类的 pow 方法做运算时，不使用任何 Math 对象：`Math.pow(x, a)`
- 静态方法通过类名调用
- 可以认为静态方法是没有 this 参数的方法。
- 静态方法可以不能访问对象的实例域，可以访问自身类中的静态域
- 可以使用对象调用静态方法，但是不建议这样使用
```java
public static int getNextId(){
  return nextId;
}
```
两种使用静态方法的情况：
- 一个方法不需要访问对象的状态，其所需要的参数都是通过显式参数提供
- 一个方法只需要访问类的静态域

#### 工厂方法
？？

#### main 方法
main 方法也是一个静态方法。
```java
public static void main(String[] args){
  //construct object here
}
```
main 方法不对任何对象操作。实际上，在启动程序时还没有任何一个对象。静态的 main 方法将执行并创建程序所需要的对象。

每一个类可以有一个 main 方法。这是一个常用于对类进行单元测试的技巧。

## 方法参数
有关将参数传递给方法（或函数）的一些术语：
- 按值调用：方法接收的是调用者提供的**值**
- 按引用调用：方法接收的是调用者提供的变量**地址**

Java 程序设计中方法参数的使用情况：
- 一个方法不能修改一个基本数据类型的参数
- 一个方法可以改变一个对象参数的状态
- 一个方法不能让对象参数引用一个新的变量

## 对象构造
对象的构造非常重要，所以 Java 提供了多种编写构造器的方式。

#### 重载
重载：如果多个方法有相同的名字、不同的参数，便产生了重载。

重载解析：编译器必须挑选出具体执行哪个方法，它通过用各种方法给出的参数类型与特定方法调用所使用的值类型进行匹配来挑选出相应的方法。如果编译器找不到匹配的参数，就会产生编译时错误，因为根本不存在匹配，或者没有一个其他的更好。

签名：方法名和参数类型构成方法的签名。Java 不只允许构造器方法的重载，它允许重载任何方法。因此要完整地描述一个方法，需要指出方法名以及参数类型，即方法的签名。返回类型不是方法签名的一部分。

#### 默认域初始化
如果在构造器中没有显式地给域赋值，那么就会被自动地赋为默认值
|类型|数值|布尔值|对象引用|
|:-:|:-:|:-:|:-:|
|默认值|0|false|null|

如果不明确地对域进行初始化，会影响程序代码的可读性。这是一种缺少程序设计经验的表现。

#### 无参数的构造器
仅当类没有提供任何构造器时，系统才会提供一个默认的构造器
- 如果编写一个类时没有编写构造器，系统会提供一个无参数的构造器。这个构造器将所有的实例域设置为默认值。
- 如果类中提供了至少一个构造器，但是没有提供无参数的构造器，则在构造对象时如果没有提供参数就会被视为不合法。

#### 显式域初始化
可以在类中，直接将一个值赋给任何域
- 确保不管怎样调用构造器，每个实例域都可以被设置为一个有意义的初值。这是一种很好的设计习惯。
- 当一个类的所有构造器都希望把相同的值赋予某个特定的实例域时，这种方法特别有用
- 初始值不一定是常量，可以调用方法对域进行初始化
```java
class Employee{
  private static int nextId;
  private int id = assingId();
  ...
  private static int assignId(){
    int r = netId;
    nextId++;
    return r;
  }
  ...
}
```
#### 参数名
几种常用的为参数命名技巧
- 参数用单个字符命名：只有阅读代码才能够了解参数的含义
- 在每个参数名前面加一个前缀「a」：清晰，一眼就能看懂参数的含义
- 参数变量用同样的名字将实例域**屏蔽**起来，使用 this 关键字访问实例域
```java
public Employee(String n,double s){
  name = n;
  salary = s;
}

public Employee(String aName,double aSalary){
  name = aName;
  salary = aSalary;
}

public Employee(String name,double salary){
  this.name = name;
  this.salary = salary;
}
```

#### 调用另一个构造器
this 关键字还有另一个含义。如果**构造器**的**第一个**语句形如 `this(...)`，这个构造器将调用同一个类的另一个构造器。
```java
public Employee(double s){
  //calls Employee(String,double)
  this("Employee #" + nextId, s);
  nextId++;
}
```
- 当调用 new Employee(60000) 时，Employee(double) 构造器将调用 Employee(String, double)构造器
- 采用这种方式使用 this 关键字非常有用，这样对于公共的构造器代码部分只编写一次即可

#### 初始化块
在一个类的声明中，可以包含多个代码块。只要构造类的对象，这些块就会执行。<br>
这种机制不是必需的，也不常见。通常，直接将初始化代码放在构造器中。

调用构造器的具体处理步骤：
1. 所有数据域被初始化为默认值
2. 按照在类申明中出现的次序，依次执行所有域初始化语句和初始化块
3. 如果构造器的第一行调用了第二个构造器，则执行第二个构造器的主体
4. 执行这个构造器的主体

在类的第一次加载的时候，将会进行静态域的初始化
- 如果没有显式地设置为其他值，则设为默认值
- 如果对类的静态域进行初始化的代码比较复杂，那么可以用静态的初始化块
- 所有的静态初始化语句以及静态初始化块都将依照类定义的顺序执行
```java
static{
  Random generator = new Random();
  nextId = generator.nextInt(10000)
}
```

#### 对象析构与 finalize 方法
由于 Java 有自动的垃圾回收器，不需要人工回收内存，所以 Java 不支持析构器。

某些对象除了使用内存，还使用了其他资源，当资源不再需要时，将其回收和再利用显得十分重要。<br>
可以为任何一个类添加 finalize 方法。finalize 方法将在垃圾回收器清除对象之前调用。在实际应用中，不要依赖 finalize 方法回收任何短缺的资源，因为很难直到这个方法什么时候才能够调用。

如果某个资源需要在使用完毕后立刻被关闭，那么就需要人工来管理。对象用完时可以应用一个 close 方法来完成相应的清理操作。

## 包
#### 类的导入

#### 静态导入

#### 将类放入包中

#### 包作用域

## 类路径

## 文档注释
#### 注释的插入

#### 类注释

#### 方法注释

#### 域注释

#### 通用注释

#### 包与概述注释

#### 注释的抽取

## 类设计技巧
- 一定要保证数据私有
- 一定要对数据初始化
- 不要在类中使用过多的基本类型
- 不是多有的域都需要独立的域访问器和域更改器
- 将职责过多的类进行分解
- 类名和方法名要能够体现它们的职责
