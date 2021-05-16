# Java笔记

## 基础语法
[1.基本数据结构](#1.基本数据结构)
[2.方法](#2.方法)
[3.递归](#3.递归)

## 面向对象
[1.面向对象的概念](#1.面向对象的概念)
[2.构造方法](#2.构造方法)
[3.静态和实例](#3.静态和实例)
[4.初始化块](#4.初始化块)
[5.关键字this](#5.关键字this)
[6.可见性修饰符和数据域封装](#6.可见性修饰符和数据域封装)
[7.字符串](#7.字符串)
[8.继承](#8.继承)
[9.Object类的部分方法](#9.Object类的部分方法)
[10.抽象类和接口](#10.抽象类和接口)
[11.基本数据类型和包装类](#11.基本数据类型和包装类)
[12.面向对象思想](#12.面向对象思想)
[13.序列化和反序列化](#13.序列化和反序列化)
[14.反射机制](#14.反射机制)

## 异常处理
[1.异常处理](#1.异常处理)

## Java虚拟机
[1.运行时数据区域](#1.运行时数据区域)
[2.垃圾回收](#2.垃圾回收)

## 多线程
[1.进程和线程](#1.进程和线程)
[2.关键字synchronized和volatile](#2.关键字synchronized和volatile)
[3.多线程相关的方法](#3.多线程相关的方法)
[4.线程池](#4.线程池)

## 容器

[1.Iterable接口和Iterator接口](#1.Iterable接口和Iterator接口)
[2.Collection接口](#2.Collection接口)
[3.线性表](#3.线性表)
[4.映射和集合](#4.映射和集合)

# 基础语法

## 1.基本数据结构

Java 的基本数据类型有 8 种，包括 6 种数字类型、1 种字符类型和 1 种布尔类型。

### 基本数据类型总览

数字类型包括 4 种整数类型和 2 种浮点数类型，4 种整数类型是 byte、short、int 和 long，2 种浮点数类型是 float 和 double。

字符类型是 char，用于表示单个字符。Java 使用统一码对字符进行编码。

布尔类型是 boolean，包括 true 和 false 两种取值。

![](https://tva1.sinaimg.cn/large/008i3skNly1gq96c6kp6nj318g0rgta7.jpg)

### 数字类型直接量

直接量是在程序中直接出现的常量值。

将整数类型的直接量赋值给整数类型的变量时，只要直接量没有超出变量的取值范围，即可直接赋值，如果直接量超出了变量的取值范围，则会导致编译错误。

整数类型的直接量默认是 int 类型，如果直接量超出了 int 类型的取值范围，则必须在其后面加上字母 L 或 l，将直接量显性声明为 long 类型，否则会导致编译错误。

浮点类型的直接量默认是 double 类型，如果要将直接量表示成 float 类型，则必须在其后面加上字母 F 或 f。将 double 类型的直接量赋值给 float 类型的变量是不允许的，会导致编译错误。

### 基本数据类型之间的转换

有时需要把不同类型的值混合运算，因此需要对数据类型进行转换。

数字类型转换

不同的数字类型对应不同的范围，按照范围从小到大的顺序依次是：byte、short、int、long、float、double。

将小范围类型的变量转换为大范围类型称为拓宽类型，不需要显性声明类型转换。将大范围类型的变量转换为小范围类型称为缩窄类型，必须显性声明类型转换，否则会导致编译错误。

字符类型与数字类型之间的转换

字符类型与数字类型之间可以进行转换。

将数字类型转换成字符类型时，只使用整数的低 16 位（浮点数类型将整数部分转换成字符类型）。

将字符类型转换成数字类型时，字符的统一码转换成指定的数值类型。如果字符的统一码超出了转换成的数值类型的取值范围，则必须显性声明类型转换。

布尔类型不能与其他基本数据类型进行转换

布尔类型不能转换成其他基本数据类型，其他基本数据类型也不能转换成布尔类型。

## 2.方法

Java 中的方法，在其他语言中也可能被称为过程或函数，是为执行一个操作而组合在一起的语句组。如果一个操作会被多次执行，则可以将该操作定义成一个方法，执行该操作的时候调用方法即可。

### 方法的语法结构

方法包括方法头和方法体，方法头又可以分成修饰符、返回值类型、方法名和参数列表，因此方法包括 5 个部分。

- 修饰符：修饰符是可选的，告诉编译器如何调用该方法。
- 返回值类型：方法可以返回一个值，此时返回值类型是方法要返回的值的数据类型。方法也可以没有返回值，此时返回值类型是 void。
- 方法名：方法的实际名称。
- 参数列表：定义在方法头中的变量称为形式参数或参数，简称形参。当调用方法时，需要给参数传递一个值，称为实际参数，简称实参。参数列表指明方法中的参数类型、次序和数量。参数是可选的，方法可以不包含参数。
- 方法体：方法体包含具体的语句集合。

方法名和参数表共同构成方法签名。

### 参数的值传递

调用方法时，需要提供实参，实参必须与形参的次序相同，称为参数顺序匹配。实参必须与方法签名中的形参在次序上和数量上匹配，在类型上兼容，兼容的意思是不需要显性声明类型转换，即类型相同或者类型转换为拓宽类型。

在调用带参数的方法时，实参的值赋给形参，称为值传递。Java 中只有值传递，无论形参在方法中如何改变，实参不受影响。

- 当参数类型是基本数据类型时，传递的是实参的值，因此不能对实参进行修改。
- 当参数类型是对象时，传递的是对象的引用，此时可以对实参引用的对象进行修改，但是不能让实参引用新的对象。

### 方法的重载

方法的重载是指在同一个类中的多个方法有相同的名称，但是方法签名不同，编译器能够根据方法签名决定调用哪个方法。由于方法签名由方法名和参数表共同构成，因此方法的重载等同于多个方法有相同的名称和不同的参数列表。

方法的重载可以增加程序的可读性，执行相似操作的方法应该有相同的名称。

关于方法的重载，需要注意以下两点。

- 方法签名只由方法名和参数列表共同构成，因此被重载的方法必须具有不同的参数列表，而不能通过不同的修饰符和返回值类型进行方法的重载。
- 如果一个方法调用有多个可能的匹配，则编译器会调用最合适的匹配方法，如果编译器无法判断哪个方法最匹配，则称为歧义调用，会导致编译错误。

下面用两段示例代码说明方法的重载。

```
public class Main {
    public static void main(String[] args) {
        getSum(1, 2);
        getSum(1.5, 2.5);
        getSum(5, 5.5);
    }

    public static void getSum(int num1, int num2) {
        System.out.println(num1 + "+" + num2 + "=" + (num1 + num2));
    }

    public static void getSum(double num1, double num2) {
        System.out.println(num1 + "+" + num2 + "=" + (num1 + num2));
    }
}
```

```
public class Main {
    public static void main(String[] args) {
        getSum(1, 2);// 歧义调用，编译错误
    }

    public static void getSum(int num1, double num2) {
        System.out.println(num1 + "+" + num2 + "=" + (num1 + num2));
    }

    public static void getSum(double num1, int num2) {
        System.out.println(num1 + "+" + num2 + "=" + (num1 + num2));
    }
}
```

在示例 1 中，getSum(1, 2) 调用的是参数为两个 int 型的方法，getSum(1.5, 2.5) 和 getSum(5, 5.5) 调用的是参数为两个 double 型的方法，因此运行上述代码得到的输出结果是：

```
1+2=3
1.5+2.5=4.0
5.0+5.5=10.5
```

在示例 2 中，getSum(1, 2) 可以同时匹配两个方法，任何一个方法都不比另一个方法更匹配，因此为歧义调用，导致编译错误。

## 3.递归

程序调用自身的编程技巧称为递归。递归方法是直接或间接调用自身的方法。

### 递归的要点

定义递归方法时，需要定义递归的初始状态、初始状态的处理和递归调用。

初始状态也称为终止条件，即最简单的情况，此时应该直接给出如何处理初始状态。

对于非初始状态，则需要进行递归调用，对子问题进行求解，直到初始状态，然后将结果返回给调用者，直到传回原始的调用者。

递归必须定义初始状态，且保证所有的递归调用都能到达初始状态，否则会发生无限递归，导致栈溢出。

### 递归的优点

递归的优点是代码简洁且易于理解。如果问题满足递归的特点，即可以分解成子问题且子问题与原始问题相似，则可以使用递归给出自然、直接、简单的解法。

### 递归的缺点

- 时间和空间的消耗比较大。每一次函数调用都需要在内存栈中分配空间，对栈的操作还需要时间，因此时间复杂度和空间复杂度都会比较高。
- 如果子问题之间存在重叠，则在不加记忆化的情况下，递归会产生重复计算，导致时间复杂度过高。
- 由于栈的空间有限，如果递归调用的次数太多，则可能导致调用栈溢出。

### 尾递归

当递归调用是方法中最后执行的语句且它的返回值不属于表达式的一部分时，这个递归调用就是尾递归。

尾递归的特点是在返回时直接传回原始的调用者，而不用经过中间的调用者，这个特点很重要，因为大多数现代的编译器会利用该特点自动生成优化的代码。

使用尾递归代替普通的递归，可以在时间和空间方面都带来显著的提升。

### 示例代码

以下代码是计算斐波那契数的普通递归和尾递归的实现。

使用普通递归，会产生大量重复计算，导致时间复杂度过高。

使用尾递归，则不会有重复计算。

```
public class Fibonacci {
    public static long fibonacci(long index) {
        if (index <= 1) {
            return index;
        } else {
            return fibonacci(index - 1) + fibonacci(index - 2);
        }
    }

    public static long fibonacciTailRecursion(long index) {
        return fibonacciTailRecursion(index, 0, 1);
    }

    public static long fibonacciTailRecursion(long index, int curr, int next) {
        if (index == 0) {
            return curr;
        } else {
            return fibonacciTailRecursion(index - 1, next, curr + next);
        }
    }
}
```

# 面向对象

## 1.面向对象的概念

### 面向对象和面向过程的区别

面向过程：将问题分解成步骤，然后按照步骤实现函数，执行时依次调用函数。数据和对数据的操作是分离的。

面向对象：将问题分解成对象，描述事物在解决问题的步骤中的行为。对象与属性和行为是关联的。

面向过程的优点是性能比面向对象高，不需要面向对象的实例化；缺点是不容易维护、复用和扩展。

面向对象的优点是具有封装、继承、多态的特性，因而容易维护、复用和扩展，可以设计出低耦合的系统；缺点是由于需要实例化对象，因此性能比面向过程低。

### 对象和类

对象是现实世界中可以明确标识的实体，对象有自己独有的状态和行为。对象的状态由数据域的集合构成，对象的行为由方法的集合构成。

类是定义同一类型对象的结构，是对具有相同特征的对象的抽象。类是一个模板，用来定义对象的数据域和方法。可以从一个类创建多个对象，创建对象称为实例化。

## 2.构造方法

构造方法是一种特殊的方法，调用构造方法可以创建新对象。构造方法可以执行任何操作，实际应用中，构造方法一般用于初始化操作，例如初始化对象的数据域。

### 定义和调用构造方法

构造方法的名称必须和构造方法所在类的名称相同。构造方法可以被重载，即允许在同一个类中定义多个参数列表不同的构造方法。

使用 new 操作符调用构造方法，通过调用构造方法创建对象。

### 默认构造方法

类可以不显性声明构造方法。此时类中隐性声明了一个方法体为空的没有参数的构造方法，称为默认构造方法。只有当类中没有显性声明任何构造方法时，才会有默认构造方法。

### 构造方法与普通方法的区别

构造方法与普通方法有三点区别。

- 构造方法的名称必须与所在的类的名称相同。
- 构造方法没有返回类型，包括没有 void。
- 构造方法通过 new 操作符调用，通过调用构造方法创建对象。

### 示例代码

以下代码定义了一个类 Square，该类描述正方形。

每个正方形都包含边长的数据域，确定边长以后即可确定正方形的大小。

类中有两个构造方法，无参数构造方法创建边长为 1 的正方形对象，有参数构造方法创建指定边长的正方形对象。

类中有两个方法 getPerimeter 和 getArea，分别计算正方形的周长和面积。

```
class Square {
    int side = 1;

    public Square() {
    }

    public Square(int newSide) {
        side = newSide;
    }

    public int getPerimeter() {
        return side * 4;
    }

    public int getArea() {
        return side * side;
    }
}
```

## 3.静态和实例

Java 的类成员（成员变量、方法等）可以是静态的或实例的。使用关键字 static 修饰的类成员是静态的类成员，不使用关键字 static 修饰的类成员则是实例的类成员。

### 静态和实例的区别

1. 外部调用

从外部调用静态的类成员时，可以通过类名调用，也可以通过对象名调用。从外部调用实例的类成员，则只能通过对象名调用。

例如对于字符串类型 String，方法 format 是静态的，可以通过 String.format 调用，而方法 length 是实例的，只能通过 str.length 调用，其中 str 是 String 类型的实例。

建议通过类名调用静态的类成员，因为通过类名调用静态的类成员是不需要创建对象的，而且可以提高代码的可读性。

2. 内部访问

静态方法只能访问静态的类成员，不能访问实例的类成员。实例方法既可以访问实例的类成员，也可以访问静态的类成员。

为什么静态方法不能访问实例的类成员呢？因为实例的类成员是依赖于具体对象（实例）的，而静态方法不依赖于任何实例，因此不存在静态方法直接或间接地访问实例或实例的类成员的情况。

### 判断使用静态或实例

如何判断一个类成员应该被定义成静态的还是实例的呢？取决于类成员是否依赖于具体实例。如果一个类成员依赖于具体实例，则该类成员应该被定义成实例的类成员，否则就应该被定义成静态的类成员。

例如对于字符串类 String，考虑方法 format 和方法 length。

方法 format 的作用是创建格式化的字符串，该方法不依赖于任何 String 的实例，因此是静态方法（类成员）。
方法 length 的作用是获得字符串的长度，由于字符串的长度依赖于具体字符串，因此该方法依赖于 String 的实例，是实例方法（类成员）。
对于数学类 Math，所有的类成员都不依赖于具体的实例，因此都被定义成静态的类成员。

## 4.初始化块

代码初始化块属于类成员，在加载类时或创建对象时会隐式调用代码初始块。使用初始化块的好处是可以减少多个构造器内的重复代码。

### 初始化块的分类

初始化块可以分成静态初始化块和非静态初始化块，前者在加载类时被隐式调用，后者在创建对象时被隐式调用。

### 单个类的初始化块的执行顺序

如果有初始化块，则初始化块会在其他代码之前被执行。具体而言，静态初始化块会在静态方法之前被执行，非静态初始化块会在构造器和实例方法之前被执行。

由于静态初始化块在加载类时被调用，因此静态初始化块会最先执行，且只会执行一次。

由于非静态初始化块在创建对象时被调用，因此每次创建对象时都会执行非静态初始化块以及执行构造器。非静态初始化块的执行在静态初始化块的执行之后、构造器的执行之前。

### 存在继承关系的初始化块的执行顺序

如果存在继承关系，则在对子类进行类的加载和创建对象时，也会对父类进行类的加载和创建对象。执行顺序仍然是静态初始化块、非静态初始化块、构造器，由于存在继承关系，因此情况较为复杂。

对于两个类的情况，即一个父类和一个子类，执行顺序如下。

1. 执行父类的静态初始化块。
2. 执行子类的静态初始化块。
3. 执行父类的非静态初始化块。
4. 执行父类的构造器。
5. 执行子类的非静态初始化块。
6. 执行子类的构造器。

更一般的情况，对于多个类之间的继承关系（可能超过两个类，例如 B 继承了 A，C 继承了 B），执行顺序如下。

1. 按照从父类到子类的顺序，依次执行每个类的静态初始化块。
2. 按照从父类到子类的顺序，对于每个类，依次执行非静态初始化块和构造器，然后执行子类的非静态初始化块和构造器，直到所有类执行完毕。

### 示例代码

以下代码可以说明初始化块和构造器的执行顺序。代码中定义了四个类，分别是 Main、Class1、Class2 和 Class3，其中 Class2 是 Class1 的子类，Class3 是 Class2 的子类，每个类都有静态初始化块、非静态初始化块和构造器。静态方法 main 定义在 Main 中，创建了 Class3 的实例。

```
public class Main {
    static {
        System.out.println("Static initialization of Main");
    }

    {
        System.out.println("Instance initialization of Main");
    }

    public Test() {
        System.out.println("Constructor of Main");
    }

    public static void main(String[] args) {
        new Class3();
    }
}

class Class1 {
    static {
        System.out.println("Static initialization of Class1");
    }

    {
        System.out.println("Instance initialization of Class1");
    }

    Class1() {
        System.out.println("Constructor of Class1");
    }
}

class Class2 extends Class1 {
    static {
        System.out.println("Static initialization of Class2");
    }

    {
        System.out.println("Instance initialization of Class2");
    }

    Class2() {
        System.out.println("Constructor of Class2");
    }
}

class Class3 extends Class2 {
    static {
        System.out.println("Static initialization of Class3");
    }

    {
        System.out.println("Instance initialization of Class3");
    }

    Class3() {
        System.out.println("Constructor of Class3");
    }
}
```

运行代码得到的输出结果是：

```
Static initialization of Main
Static initialization of Class1
Static initialization of Class2
Static initialization of Class3
Instance initialization of Class1
Constructor of Class1
Instance initialization of Class2
Constructor of Class2
Instance initialization of Class3
Constructor of Class3
```

由于没有创建 Main 的实例，因此 Main 的非静态初始化块不会被执行，但是由于程序的入口即静态方法 main 定义在 Main 中，因此 Main 的静态初始化块首先被执行。

在方法 main 中创建了 Class3 的实例，按照父类到子类的顺序，依次执行每个类的静态初始化块，因此 Class1、Class2 和 Class3 的静态初始化块被依次执行。

在所有类的静态初始化块被执行之后，按照父类到子类的顺序，依次执行每个类的非静态初始化块和构造器，因此按照 Class1、Class2 和 Class3 的顺序，每个类的非静态初始化块和构造器被执行。

## 5.关键字this

关键字 this 代表当前对象的引用。当前对象指的是调用类中的属性或方法的对象。

### 关键字 this 用于引用隐藏变量

在方法和构造方法中，可能将属性名用作参数名，在这种情况下，需要引用隐藏的属性名才能给属性设置新值。例如，当属性名和参数名都是 var 时，需要通过 this.var = var 对属性进行赋值。

当方法内部有局部变量和属性名相同时，同样需要通过关键字 this 引用对象的属性。

如果方法内部不存在和属性名相同的局部变量，则在使用属性时，属性前面的 this 可以省略。

### 关键字 this 用于调用其他构造方法

在构造方法中，可以通过关键字 this 调用其他构造方法，具体用法是 this(参数列表)。

Java 要求，在构造方法中如果使用关键字 this 调用其他构造方法，则 this(参数列表) 语句必须出现在其他语句之前。

### 关键字 this 不能在静态代码块中使用

由于关键字 this 代表的是对象的引用，因此依赖于具体对象，而静态方法和静态初始化块不依赖于类的具体对象，因此静态方法和静态初始化块中不能使用关键字 this。

### 示例代码

第 2 节的示例代码定义了一个类 Square。使用关键字 this，可以将类 Square 按照如下方式实现。

在有参数构造方法中，关键字 this 的作用是引用隐藏变量。在无参数构造方法中，关键字 this 的作用是调用有参数构造方法。

在方法中，通过关键字 this 引用对象的属性。由于两个方法 getPerimeter 和 getArea 中都没有局部变量和对象的属性名相同，因此这两个方法中的 this.side 都可以简写为 side。

```
class Square {
    int side;

    public Square() {
        this(1);
    }

    public Square(int side) {
        this.side = side;
    }

    public int getPerimeter() {
        return this.side * 4;
    }

    public int getArea() {
        return this.side * this.side;
    }
}
```

## 6.可见性修饰符和数据域封装

Java 的可见性修饰符用于控制对类成员的访问。可见性修饰符包括 public、private、protected 和默认修饰符，此处介绍 public、private 和默认修饰符，protected 将在继承和多态部分介绍。

### 不同的可见性修饰符的含义

可见性修饰符 public 表示类成员可以在任何类中访问。

可见性修饰符 private 表示类成员只能从自身所在的类中访问。

如果不加任何可见性修饰符，则称为默认修饰符，表示类成员可以在同一个包里的任何类中访问，此时也称为包私有或包内访问。

以上三种可见性修饰符定义的类成员的可见性如下面的表格所示。

![](https://tva1.sinaimg.cn/large/008i3skNly1gqacnkpwd1j318e08it8u.jpg)

### 数据域封装

可见性修饰符可以用于控制对类成员的访问，也可以用于对数据域进行封装。

数据域封装的含义是，对数据域使用 private 修饰符，将数据域声明为私有域。如果不使用数据域封装，则数据域的值可以从类的外部直接修改，导致数据被篡改以及类难以维护。使用数据域封装的目的是为了避免直接修改数据域的值。

在定义私有数据域的类之外，不能通过直接引用的方式访问该私有数据域，但是仍然可能需要读取和修改数据域的值。为了能够读取私有数据域的值，可以编写 get 方法（称为读取器或访问器）返回数据域的值。为了能够修改私有数据域的值，可以编写 set 方法（称为设置器或修改器）将数据域的值设置为新值。

### 示例代码

在第 5 节的示例代码中，数据域没有加可见性修饰符，其可见性为默认。为了避免从类的外部直接访问和修改数据域的值，需要对数据域加 private 修饰符。为了能从类的外部得到数据域的值，需要编写 get 方法返回数据域的值。

使用数据域封装的代码如下。

```
class Square {
    private int side;

    public Square() {
        this(1);
    }

    public Square(int side) {
        this.side = side;
    }

    public int getSide() {
        return this.side;
    }

    public int getPerimeter() {
        return this.side * 4;
    }

    public int getArea() {
        return this.side * this.side;
    }
}
```

## 7.字符串

字符串是常用的数据类型。在 Java 中，常见的字符串类型包括 String、StringBuffer 和 StringBuilder。

### String

从 String 的源码可以看到，String 使用数组存储字符串的内容，数组使用关键词 final 修饰，因此数组内容不可变，使用 String 定义的字符串的值也是不可变的。

由于 String 类型的值不可变，因此每次对 String 的修改操作都会创建新的 String 对象，导致效率低下且占用大量内存空间。

### StringBuffer 和 StringBuilder

StringBuffer 和 StringBuilder 都是 AbstractStringBuilder 的子类，同样使用数组存储字符串的内容，由于数组没有使用关键词 final 修饰，因此数组内容可变，StringBuffer 和 StringBuilder 都是可变类型，可以对字符串的内容进行修改，且不会因为修改而创建新的对象。

在需要经常对字符串的内容进行修改的情况下，应使用 StringBuffer 或 StringBuilder，在时间和空间方面都显著优于 String。

StringBuffer 和 StringBuilder 有哪些区别呢？从源码可以看到，StringBuffer 对定义的方法或者调用的方法使用了关键词 synchronized 修饰，而 StringBuilder 的方法没有使用关键词 synchronized 修饰。由于 StringBuffer 对方法加了同步锁，因此其效率略低于 StringBuilder，但是在多线程的环境下，StringBuilder 不能保证线程安全，因此 StringBuffer 是更优的选择。

### 总结

1. String 是不可变类型，每次对 String 的修改操作都会创建新的 String 对象，导致效率低下且占用大量内存空间，因此 String 适用于字符串常量的情形，不适合需要对字符串进行大量修改的情形。
2. StringBuffer 是可变类型，可以修改字符串的内容且不会创建新的对象，且 StringBuffer 是线程安全的，适用于多线程环境。
3. StringBuilder 是可变类型，与 StringBuffer 相似，在单线程环境下 StringBuilder 的效率略高于 StringBuffer，但是在多线程环境下 StringBuilder 不保证线程安全，因此 StringBuilder 不适合多线程环境。

## 8.继承

在面向对象程序设计中，可以从已有的类（父类）派生出新类（子类），称为继承。

### 父类和子类

如果已有的类 C1 派生出一个新类 C2，则称 C1 为 C2 的父类，C2 为 C1 的子类。子类从父类中继承可访问的类成员，也可以添加新的类成员。子类通常包含比父类更多的类成员。

继承用来为 is-a 关系建模，子类和父类之间必须存在 is-a 关系。

如果一个类在定义时没有指定继承，它的父类默认是 Object。

### 关键字 super

关键字 super 指向当前类的的父类。关键字 super 可以用于两种途径，一是调用父类的构造方法，二是调用父类的方法。

调用父类的构造方法，使用 super() 或 super(参数)，该语句必须是子类构造方法的第一个语句，且这是调用父类构造方法的唯一方式。

调用父类的方法，使用 super.方法名(参数)。

### 构造方法链

如果构造方法没有显式地调用同一个类中其他的构造方法或父类的构造方法，将隐性地调用父类的无参数构造方法，即编译器会把 super() 作为构造方法的第一个语句。

构造一个类的实例时，将会沿着继承链调用所有父类的构造方法，父类的构造方法在子类的构造方法之前调用，称为构造方法链。

下面用一个例子说明构造方法链。考虑如下代码。

```
public class Class3 extends Class2 {
    public static void main(String[] args) {
        new Class3();
    }

    public Class3() {
        System.out.println("D");
    }
}

class Class2 extends Class1 {
    public Class2() {
        this("B");
        System.out.println("C");
    }

    public Class2(String s) {
        System.out.println(s);
    }
}

class Class1 {
    public Class1() {
        System.out.println("A");
    }
}
```

## 9.Object类的部分方法

### toString

方法定义：
```
public String toString()
```

该方法返回一个代表该对象的字符串。该方法的默认实现返回的字符串在绝大多数情况下是没有信息量的，因此通常都需要在子类中重写该方法。

### equals

方法定义：
```
public boolean equals(Object obj)
```

该方法检验两个对象是否相等。该方法的默认实现使用 == 运算符检验两个对象是否相等，通常都需要在子类中重写该方法。

### hashCode

方法定义：
```
public native int hashCode()
```

该方法返回对象的散列码。关键字 native 表示实现方法的编程语言不是 Java。

散列码是一个整数，用于在散列集合中存储并能快速查找对象。

根据散列约定，如果两个对象相同，它们的散列码一定相同，因此如果在子类中重写了 equals 方法，必须在该子类中重写 hashCode 方法，以保证两个相等的对象对应的散列码是相同的。

两个相等的对象一定具有相同的散列码，两个不同的对象也可能具有相同的散列码。实现 hashCode 方法时，应避免过多地出现两个不同的对象也可能具有相同的散列码的情况。

### finalize

方法定义：
```
protected void finalize() throws Throwable
```

该方法用于垃圾回收。如果一个对象不再能被访问，就变成了垃圾，finalize 方法会被该对象的垃圾回收程序调用。该方法的默认实现不做任何事，如果必要，子类应该重写该方法。

该方法可能抛出 Throwable 异常。

### clone

方法定义：
```
protected native Object clone() throws CloneNotSupportedException
```

该方法用于复制一个对象，创建一个有单独内存空间的新对象。

不是所有的对象都可以复制，只有当一个类实现了 java.lang.Cloneable 接口时，这个类的对象才能被复制。

该方法可能抛出 CloneNotSupportedException 异常。

### getClass

方法定义：
```
public final native Class<?> getClass()
```

该方法返回对象的元对象。元对象是一个包含类信息的对象，包括类名、构造方法和方法等。

一个类只有一个元对象。每个对象都有一个元对象，同一个类的多个对象对应的元对象相同。

## 10.抽象类和接口

抽象类指抽象而没有具体实例的类。接口是一种与类相似的结构，在很多方面与抽象类相近。

### 抽象类

抽象类使用关键字 abstract 修饰。抽象类和常规类一样具有数据域、方法和构造方法，但是不能用 new 操作符创建实例。

抽象类可以包含抽象方法。抽象方法使用关键字 abstract 修饰，只有方法签名而没有实现，其实现由子类提供。抽象方法都是非静态的。包含抽象方法的类必须声明为抽象类。

非抽象类不能包含抽象方法。如果一个抽象父类的子类不能实现所有的抽象方法，则该子类也必须声明为抽象类。

包含抽象方法的类必须声明为抽象类，但是抽象类可以不包含抽象方法。

### 接口

接口使用关键字 interface 定义。接口只包含可见性为 public 的常量和抽象方法，不包含变量和具体方法。

和抽象类一样，接口不能用 new 操作符创建实例。

新版本的 JDK 关于接口的规则有以下变化。

从 Java 8 开始，接口方法可以由默认实现。
从 Java 9 开始，接口内允许定义私有方法。
一个类只能继承一个父类，但对接口允许多重继承。一个接口可以继承多个接口，这样的接口称为子接口。

### 抽象类和接口的区别

- 抽象类的变量没有限制，接口只包含常量，即接口的所有变量必须是 public static final。
- 抽象类包含构造方法，子类通过构造方法链调用构造方法，接口不包含构造方法。
- 抽象类的方法没有限制，接口的方法必须是 public abstract 的实例方法（注：新版本的 JDK 关于接口的规则有变化，见上文）。
- 一个类只能继承一个父类，但是可以实现多个接口。一个接口可以继承多个接口。

### 自定义比较方法

有两个接口可以实现对象之间的排序和比较大小。

Comparable 接口是排序接口。如果一个类实现了 Comparable 接口，则该类的对象可以排序。Comparable 接口包含一个抽象方法 compareTo，实现 Comparable 接口的类需要实现该方法，定义排序的依据。

Comparator 接口是比较器接口。如果一个类本身不支持排序（即没有实现 Comparable 接口），但是又需要对该类的对象排序，则可以通过实现 Comparator 接口的方式建立比较器。Comparator 接口包含两个抽象方法 compare 和 equals，其中 compare 方法是必须在实现类中实现的，而 equals 方法在任何类中默认已经实现。

如果需要对一个数组或列表中的多个对象进行排序，则可以将对象的类定义成实现 Comparable 接口，也可以在排序时定义 Comparator 比较器。

## 11.基本数据类型和包装类

Java 有 8 种基本数据类型，基本数据类型不属于对象。但是在很多时候需要把对象作为参数，因此需要把基本数据类型包装成对象，对应的类称为包装类。

### 基本数据类型和包装类的对应关系

每种基本数据类型都有对应的包装类，如以下表格所示。

![](https://tva1.sinaimg.cn/large/008i3skNly1gqfr2h9atkj318g0j40u8.jpg)

包装类的名称和对应的基本数据类型相同，包装类的名称的首字母大写，Integer 和 Character 例外。

### 包装类的构造方法

可以通过包装类的构造方法创建包装对象。调用构造方法时，构造方法的参数值可以是基本数据类型的值，也可以是表示值的字符串。

包装类的构造方法都是有参数的，没有无参数构造方法。

包装类的实例都是不可变的，一旦创建了包装对象，其内部的值就不能再改变。

### 自动装箱和自动拆箱

从 JDK 1.5 开始，基本数据类型和包装类之间可以进行自动转换。
将基本数据类型的值转换为包装对象，称为装箱。将包装对象转换为基本数据类型的值，称为拆箱。

## 12.面向对象思想

### 类的关系

#### 关联

关联是一种描述两个类之间行为的一般二元关系。

关联中的每个类可以指定一个数字或一个数字区间，表示该关联涉及类中的多少个对象。

在 Java 代码中，关联可以用数据域和方法进行实现，一个类中的方法包含另一个类的参数。

下面的代码是关联的例子。储户在银行开账户是储户类 Depositor 和银行类 Bank 之间的关联。每个储户可以在多个银行开设账户，每个银行也可以有多个储户在该银行开设账户。

```
class Depositor {
    private List<Bank> bankList;

    public Depositor() {
        bankList = new ArrayList<Bank>();
    }

    public void addBank(Bank account) {
        bankList.add(account);
    }
}
```

```
class Bank {
    private List<Depositor> depositorList;

    public Bank() {
        depositorList = new ArrayList<Depositor>();
    }

    public void addUser(Depositor depositor) {
        depositorList.add(depositor);
    }
}
```

#### 聚集和组合

聚集是一种特殊的关联形式，表示两个对象之间的所属关系。聚集模拟具有（has-a）关系。

所有者对象称为聚集对象，对应的类称为聚集类；从属对象称为被聚集对象，对应的类称为被聚集类。

一个对象可以被几个聚集对象所拥有。如果一个对象被一个聚集对象所专有，该对象和聚集对象之间的关系就称为组合。

下面的代码是聚集和组合的例子。司机类 Driver 是聚集类，汽车类 Car 和身份证类 IDCard 是被聚集类。每个司机驾驶一辆汽车，并拥有一张身份证。由于一辆汽车可以被多个司机驾驶，因此 Driver 和 Car 之间的关系是聚集关系。由于一张身份证只能被一个人拥有，因此 Driver 和 IDCard 之间的关系是组合关系。

```
class Driver {
    private Car car;
    private IDCard idCard;
}
```

```
class Car {
}
```

```
class IDCard {
}
```

#### 依赖

依赖指两个类之间一个类使用另一个类的关系，前者称为客户（client），后者称为供应方（supplier）。

在 Java 代码中，实现依赖的方式是，客户类中的方法包含供应方类的参数。

下面的代码是依赖的例子。Java 自带的抽象类 Calendar 包含方法 setTime，该方法包含一个 Date 类型的参数，此处 Calendar 是客户类，Date 是供应方类。

```
public abstract class Calendar implements Serializable, Cloneable, Comparable<Calendar> {
    public final void setTime(Date date) {
        setTimeInMillis(date.getTime());
    }
}
```

#### 继承

继承模拟是（is-a）关系。

强是（strong is-a）关系描述两个类之间的直接继承关系，弱是（weak is-a）关系描述一个类具有某些属性。

强是关系可以用类的继承表示，弱是关系可以用接口表示。

### 类的设计原则

#### 内聚性

同一个类/模块的所有操作应该有高度关联性，支持共同的目标，只负责一项任务，即单一责任原则，称为高内聚。

不同类/模块之间的关联程度应该尽量低，对一个类/模块的修改应该尽量减少对其他类/模块的影响，称为低耦合。

#### 封装性

类中的数据域应该使用 private 修饰符隐藏其可见性，避免从外部直接访问数据域。

如果需要从外部读取数据域的值，则提供读取器方法。如果需要从外部修改数据域的值，提供设置器方法。

如果一个方法只在类的内部使用，则应该对该方法使用 private 修饰符，避免从外部调用该方法。

#### 实例和静态

依赖于类的具体实例的数据域和方法应声明为实例数据域和实例方法，反之应声明为静态数据域和静态方法。

如果一个数据域被所有实例共享，该数据域应声明为静态数据域。如果一个方法不依赖于具体实例，该方法应声明为静态方法。

#### 继承和聚集

继承模拟是（is-a）关系，聚集模拟具有（has-a）关系。应考虑两个类之间的关系为是关系还是具有关系，决定使用继承或聚集。

![](https://tva1.sinaimg.cn/large/008i3skNly1gqfrchbcfgj30ko0aodh9.jpg)

## 13.序列化和反序列化

把对象转换成字节序列的过程称为对象的序列化，把字节序列恢复成对象的过程称为对象的反序列化。

### 可序列化接口 Serializable

只有当一个类实现了 Serializable 接口时，这个类的实例才是可序列化的。

Serializable 接口是一个标识接口，用于标识一个对象是否可被序列化，该接口不包含任何数据域和方法。

如果试图对一个没有实现 Serializable 接口的类的实例进行序列化，会抛出 NotSerializableException 异常。

将一个对象序列化时，会将该对象的数据域进行序列化，不会对静态数据域进行序列化。

### 关键字 transient

如果一个对象的类实现了 Serializable 接口，但是包含一个不可序列化的数据域，则该对象不可序列化。为了使该对象可序列化，需要给不可序列化的数据域加上关键字 transient。

如果一个数据域可序列化，但是不想将这个数据域序列化，也可以给该数据域加上关键字 transient。

在序列化的过程中，加了关键字 transient 的数据域将被忽略。

## 14.反射机制

### 反射机制

Java 反射机制的核心是在程序运行时动态加载类以及获取类的信息，从而使用类和对象的数据域和方法。

### Class 类

Class 类的作用是在程序运行时保存每个对象所属的类的信息，在程序运行时分析类。一个 Class 类型的对象表示一个特定类的属性。

有三种方法可以得到 Class 类型的实例。

第一种方法是对一个对象调用 getClass 方法，获得该对象所属的类的 Class 对象。

第二种方法是调用静态方法 Class.forName，将类名作为参数，获得类名对应的 Class 对象。

第三种方法是对任意的 Java 类型 T（包括基本数据类型、引用类型、数组、关键字 void），调用 T.class 获得类型 T 对应的 Class 对象，此时获得的 Class 对象表示一个类型，但是这个类型不一定是一种类。

三种方法中，通过静态方法 Class.forName 获得 Class 对象是最常用的。

### Class 类的常用方法

Class 类中最常用的方法是 getName，该方法返回类的名字。

Class 类中的 getFields、getMethods 和 getConstructors 方法分别返回类中所有的公有（即使用可见修饰符 public 修饰）的数据域、方法和构造方法。

Class 类中的 getDeclaredFields、getDeclaredMethods 和 getDeclaredConstructors 方法分别返回类中所有的数据域、方法和构造方法（包括所有可见修饰符）。

Class 类中的 getField、getMethod 和 getConstructor 方法分别返回类中单个的公有（即使用可见修饰符 public 修饰）的数据域、方法和构造方法。

Class 类中的 getDeclaredField、getDeclaredMethod 和 getDeclaredConstructor 方法分别返回类中单个的数据域、方法和构造方法（包括所有可见修饰符）。

![](https://tva1.sinaimg.cn/large/008i3skNly1gqfrk6kwkwj319y0b40ve.jpg)

# 异常处理

## 1.异常处理

编程错误可以分成三类：语法错误、逻辑错误和运行错误。

语法错误（也称编译错误）是在编译过程中出现的错误，由编译器检查发现语法错误。

逻辑错误指程序的执行结果与预期不符，可以通过调试定位并发现错误的原因。

运行错误是引起程序非正常终端的错误，需要通过异常处理的方式处理运行错误。

### 异常处理概念

运行错误会引起异常，如果不对异常进行捕获和处理，程序就会非正常终止，并可能引起别的问题。

为了避免程序非正常终止，保证程序的稳定性，需要使用异常处理的功能。

Java 提供了 try-catch 块的结构，用于捕获并处理异常。该结构包括 try 块和 catch 块两部分，分别以关键字 try 和 catch 开始，catch 块包含特定异常类型的参数。在 try 块中包含可能抛出异常的语句，当 try 块中的一个语句抛出异常且和 catch 块的参数的异常类型一致时，try 块中剩下的语句会被跳过，catch 块中的语句会被执行。

### 异常类型

Java 的异常类型是 Exception 类，它是 Throwable 类的子类。

Exception 类描述由程序和外部环境引起的错误，可以通过程序捕获和处理这些异常。Exception 类有多个子类，分别描述特定的异常。

RuntimeException 类是 Exception 类的子类，描述运行时异常。RuntimeException 类有多个子类，分别描述特定的运行时异常。

### 异常处理的操作

Java 的异常处理基于三种操作：声明异常、抛出异常和捕获异常。

#### 声明异常

如果一个方法可能抛出异常，则需要在方法声明中使用关键字 throws 声明异常。如果一个方法可能抛出多种类型的异常，则需要在关键字 throws 之后依次列举可能抛出的异常类型。

#### 抛出异常

如果程序检查到错误，则可以创建一个异常的实例并抛出该异常实例。使用关键字 throw 抛出异常。

需要注意声明异常的关键字 throws 和抛出异常的关键字 throw 的区别。

#### 捕获异常

捕获异常通过 try-catch 块实现。每个 catch 块包含一个特定异常类型的参数，如果需要捕获多种异常，则需要使用多个 catch 块，每个 catch 块分别包含一个特定异常类型的参数。

如果 try 块的执行过程中没有出现异常，则跳过 catch 块。

如果 try 块中的一个语句抛出一个异常，则跳过 try 块中剩下的语句，寻找可以处理该异常的代码，处理异常的代码称为异常处理器。具体而言，依次检查每个 catch 块，寻找可以处理该异常的 catch 块。

- 如果发现一个 catch 块的参数的异常类型和抛出的异常实例匹配，则将异常实例赋给该 catch 块的参数，执行该 catch 块的语句。
- 如果在当前方法中没有发现异常处理器，则异常没有被捕获和处理，退出当前的方法，并将异常传递给当前方法的调用者，继续寻找异常处理器。

如果一个 catch 块可以捕获一个父类的异常对象，则该 catch 块也能捕获该父类的所有子类的异常对象。

由于父类包含子类，因此需要注意 catch 块的顺序，子类异常对应的 catch 块必须出现在父类异常的 catch 块之前，否则会出现编译错误。

### finally 子句

有时，无论异常是否出现或者被捕获，都需要执行一些语句，可以通过 finally 子句实现。使用关键字 finally 声明 finally 子句。

如果在 try-catch 块中包含 return 语句，finally 子句将在方法返回之前被执行。

```
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String str1 = scanner.next();
        String opStr = scanner.next();
        String str2 = scanner.next();
        scanner.close();
        System.out.println(calculate(str1, opStr, str2));
    }

    public static int calculate(String str1, String opStr, String str2) {
        int result = 0;
        try {
            int num1 = Integer.parseInt(str1);
            int num2 = Integer.parseInt(str2);
            char op = opStr.charAt(0);
            switch (op) {
            case '+':
                result = num1 + num2;
                break;
            case '-':
                result = num1 - num2;
                break;
            case '*':
                result = num1 * num2;
                break;
            case '/':
                result = num1 / num2;
                break;
            default:
                throw new RuntimeException("Invalid expression");
            }
            return result;
        } catch (NumberFormatException ex) {
            System.out.println("NumberFormatException");
        } catch (ArithmeticException ex) {
            System.out.println("ArithmeticException");
        } catch (Exception ex) {
            System.out.println(ex.getMessage());
        } finally {
            System.out.println("The finally block");
        }
        return result;
    }
}
```

上述代码的作用是，在命令行依次输入第一个数、运算符和第二个数，计算表达式的结果并输出。方法 calculate 根据三个参数计算结果，包含 try-catch 块和 finally 子句。

由于 Exception 类包含了 NumberFormatException 类和 ArithmeticException 类，因此 Exception 类的 catch 块必须放在 NumberFormatException 类和 ArithmeticException 类的 catch 块之后，否则会出现编译错误。

方法 calculate 中的 finally 子句在任何情况下都会执行。如果 try 块的执行过程中没有出现异常，则 finally 子句将在方法返回之前被执行。

# Java虚拟机

## 1.运行时数据区域

Java 虚拟机在执行 Java 程序的过程中会把它管理的内存划分成若干个不同的数据区域。这些区域有不同的用途。

### 程序计数器

程序计数器是一块较小的内存空间，可以看作当前线程所执行的字节码的行号指示器。字节码解释器工作时，通过改变程序计数器的值选取下一条需要执行的字节码指令，分支、循环、跳转、异常处理、线程恢复等功能都需要依赖程序计数器完成。

为了线程切换后能恢复到正确的执行位置，每个线程都需要有独立的程序计数器。由于每个线程的程序计数器是独立存储的，因此各线程之间的程序计数器互不影响，这类内存区域被称为线程私有的内存区域。

程序计数器是唯一不会出现 OutOfMemoryError 的内存区域。

### Java 虚拟机栈

和程序计数器一样，Java 虚拟机栈也是线程私有的，它的生命周期与线程相同。

虚拟机栈描述的是 Java 方法执行的内存模型，每个方法被执行的时候会创建一个栈帧，用于存储局部变量表、操作栈、动态链接、方法出口等信息。一个方法被调用直至执行完成的过程对应一个栈帧在虚拟机中从入栈到出栈的过程。

局部变量表存放编译器可知的各种基本数据类型、对象引用类型和返回地址类型。

Java 虚拟机栈会出现两种异常。

- 如果虚拟机栈不可以动态扩展，当线程请求的栈深度大于虚拟机所允许的深度时，将抛出 StackOverflowError 异常；
- 如果虚拟机栈可以动态扩展，当无法申请到足够的内存时，将抛出 OutOfMemoryError 异常。

### 本地方法栈

本地方法栈和虚拟机栈的作用相似。区别在于，虚拟机栈为虚拟机执行 Java 方法服务，本地方法栈为虚拟机使用到的本地方法服务。有的虚拟机（如 HotSpot 虚拟机）把本地方法栈和虚拟机栈合二为一。

和虚拟机栈一样，本地方法栈也会出现 StackOverflowError 和 OutOfMemoryError 两种异常。

### Java 堆

对于大多数应用而言，Java 堆是 Java 虚拟机管理的内存中最大的一块。Java 堆是被所有线程共享的内存区域，其目的是存放对象实例，几乎所有的对象实例都在堆中分配内存。

Java 堆是垃圾回收器管理的主要内存，因此也称为 GC 堆（Garbage Collected Heap）。从垃圾回收的角度，由于现代编译器基本都采用分代垃圾回收算法，所以 Java 堆还可以分成新生代和老年代，新生代又可以细分成 Eden 区、From Survivor 区、To Survivor 区等。细分成多个空间的目的是更好地回收内存或者更快地分配内存。

### 方法区

和 Java 堆一样，方法区也是被所有线程共享的内存区域。方法区用于存储已经被虚拟机加载的类信息、常量、静态变量、即时编译器编译后的代码等数据。

当方法区无法满足内存分配需求时，将抛出 OutOfMemoryError 异常。

JDK 1.8 将方法区彻底移除，取而代之的是元空间，元空间使用的是直接内存。

### 运行时常量池

运行时常量池是方法区的一部分。Class 文件中除了有类的版本、字段、方法、接口等描述信息外，还有常量池信息，用于存放编译器生成的字面量和符号引用，这些信息将在类加载后存放到方法区的运行时常量池中。

运行时常量池也受到方法区内存的限制，当常量池无法再申请到内存时将抛出 OutOfMemoryError 异常。

### 直接内存

直接内存不是虚拟机运行时数据区域的一部分，也不是虚拟机规范中定义的内存区域，但是这部分也被频繁地使用，而且也可能导致 OutOfMemoryError 异常出现。

本机直接内存的分配不受到 Java 堆大小的限制，但是直接内存仍然受到本机总内存地大小及处理器寻址空间的限制。如果各个内存区域的总和大于物理内存限制，就会导致动态扩展时出现 OutOfMemoryError 异常。

## 2.垃圾回收

垃圾回收，顾名思义就是释放垃圾占用的空间，从而提升程序性能，防止内存泄露。当一个对象不再被需要时，该对象就需要被回收并释放空间。

Java 内存运行时数据区域包括程序计数器、虚拟机栈、本地方法栈、堆等区域。其中，程序计数器、虚拟机栈和本地方法栈都是线程私有的，当线程结束时，这些区域的生命周期也结束了，因此不需要过多考虑回收的问题。而堆是虚拟机管理的内存中最大的一块，堆中的内存的分配和回收是动态的，垃圾回收主要关注的是堆空间。

### 调用垃圾回收器的方法

调用垃圾回收器的方法是 gc，该方法在 System 类和 Runtime 类中都存在。

在 Runtime 类中，方法 gc 是实例方法，方法 System.gc 是调用该方法的一种传统而便捷的方法。

在 System 类中，方法 gc 是静态方法，该方法会调用 Runtime 类中的 gc 方法。

其实，java.lang.System.gc 等价于 java.lang.Runtime.getRuntime.gc 的简写，都是调用垃圾回收器。

方法 gc 的作用是提示 Java 虚拟机进行垃圾回收，该方法由系统自动调用，不需要人为调用。该方法被调用之后，由 Java 虚拟机决定是立即回收还是延迟回收。

### finalize 方法

与垃圾回收有关的另一个方法是 finalize 方法。该方法在 Object 类中被定义，在释放对象占用的内存之前会调用该方法。该方法的默认实现不做任何事，如果必要，子类应该重写该方法，一般建议在该方法中释放对象持有的资源。

### 判断对象是否可回收

垃圾回收器在对堆进行回收之前，首先需要确定哪些对象是可回收的。常用的算法有两种，引用计数算法和根搜索算法。

#### 引用计数算法

引用计数算法给每个对象添加引用计数器，用于记录对象被引用的计数，引用计数为 0 的对象即为可回收的对象。

虽然引用计数算法的实现简单，判定效率也很高，但是引用计数算法无法解决对象之间循环引用的情况。如果多个对象之间存在循环引用，则这些对象的引用计数永远不为 0，无法被回收。因此 Java 语言没有使用引用计数算法。

#### 根搜索算法

主流的商用程序语言都是使用根搜索算法判断对象是否可回收。根搜索算法的思路是，从若干被称为 GC Roots 的对象开始进行搜索，不能到达的对象即为可回收的对象。

在 Java 中，GC Roots 一般包含下面几种对象：

- 虚拟机栈中引用的对象；
- 本地方法栈中的本地方法引用的对象；
- 方法区中的类静态属性引用的对象；
- 方法区中的常量引用的对象。

#### 引用的分类

引用计数算法和根搜索算法都需要通过判断引用的方式判断对象是否可回收。

在 JDK 1.2 之后，Java 将引用分成四种，按照引用强度从高到低的顺序依次是：强引用、软引用、弱引用、虚引用。

- 强引用是指在程序代码中普遍存在的引用。垃圾回收器永远不会回收被强引用关联的对象。
- 软引用描述还有用但并非必需的对象。只有在系统将要发生内存溢出异常时，被软引用关联的对象才会被回收。在 JDK 1.2 之后，提供了 SoftReference 类实现软引用。
- 弱引用描述非必需的对象，其强度低于软引用。被弱引用关联的对象只能存活到下一次垃圾回收发生之前，当垃圾回收器工作时，被弱引用关联的对象一定会被回收。在 JDK 1.2 之后，提供了 WeakReference 类实现弱引用。
- 虚引用是最弱的引用关系。一个对象是否有虚引用的存在，完全不会对其生存时间构成影响，也无法通过虚引用取得一个对象实例。为一个对象设置虚引用关联的唯一目的就是能在这个对象被回收时收到一个系统通知。在 JDK 1.2 之后，提供了 PhantomReference 类实现虚引用。

### 垃圾回收算法

#### 标记—清除算法

标记—清除算法是最基础的垃圾回收算法，后续的垃圾收集算法都是基于标记—清除算法进行改进而得到的。标记—清除算法分为“标记”和“清除”两个阶段，首先标记出所有需要回收的对象，在标记完成后统一回收所有被标记的对象。

标记—清除算法有两个主要缺点。一是效率问题，标记和清除的效率都不高，二是空间问题，标记清除之后会产生大量不连续的内存碎片，导致程序在之后的运行过程中无法为较大对象找到足够的连续内存。

#### 复制算法

复制算法是将可用内存分成大小相等的两块，每次只使用其中的一块，当用完一块内存时，将还存活着的对象复制到另外一块内存，然后把已使用过的内存空间一次清理掉。

复制算法解决了效率问题。由于每次都是对整个半区进行内存回收，因此在内存分配时不需要考虑内存碎片等复杂情况，只要移动堆顶指针，按顺序分配内存即可。复制算法的优点是实现简单，运行高效，缺点是将内存缩小为了原来的一半，以及在对象存活率较高时复制操作的次数较多，导致效率降低。

#### 标记—整理算法

标记—整理算法是根据老年代的特点提出的。标记过程与标记—清除算法一样，但后续步骤不是直接回收被标记的对象，而是让所有存活的对象都向一端移动，然后清除边界以外的内存。

#### 分代收集算法

分代收集算法根据对象的存活周期不同将内存划分为多个区域，对每个区域选用不同的垃圾回收算法。

一般把 Java 堆分为新生代和老年代。在新生代中，大多数对象的生命周期都很短，因此选用复制算法。在老年代中，对象存活率高，因此选用标记—清除算法或标记—整理算法。

### 分配内存与回收策略

Java 堆可以分成新生代和老年代，新生代又可以细分成 Eden 区、From Survivor 区、To Survivor 区等。对于不同的对象，有相应的内存分配规则。

#### Minor GC 和 Full GC

Minor GC 指发生在新生代的垃圾回收操作。因为大多数对象的生命周期都很短，因此 Minor GC 会频繁执行，一般回收速度也比较快。

Full GC 也称 Major GC，指发生在老年代的垃圾回收操作。出现了 Full GC，经常会伴随至少一次的 Minor GC。老年代对象的存活时间长，因此 Full GC 很少执行，而且执行速度会比 Minor GC 慢很多。

#### 对象优先在 Eden 区分配

大多数情况下，对象在新生代 Eden 区分配，当 Eden 区空间不够时，发起 Minor GC。

#### 大对象直接进入老年代

大对象是指需要连续内存空间的对象，最典型的大对象是那种很长的字符串以及数组。大对象对于虚拟机的内存分配而言是坏消息，经常出现大对象会导致内存还有不少空间时就提前触发垃圾回收以获取足够的连续空间分配给大对象。

将大对象直接在老年代中分配的目的是避免在 Eden 区和 Survivor 区之间出现大量内存复制。

#### 长期存活的对象进入老年代

虚拟机采用分代收集的思想管理内存，因此需要识别每个对象应该放在新生代还是老年代。虚拟机给每个对象定义了年龄计数器，对象在 Eden 区出生之后，如果经过第一次 Minor GC 之后仍然存活，将进入 Survivor 区，同时对象年龄变为 1，对象在 Survivor 区每经过一次 Minor GC 且存活，年龄就增加 1，增加到一定阈值时则进入老年代（阈值默认为 15）。

#### 动态对象年龄判定

为了能更好地适应不同程序的内存状况，虚拟机并不总是要求对象的年龄必须达到阈值才能进入老年代。如果在 Survivor 区中相同年龄的所有对象的空间总和大于 Survivor 区空间的一半，则年龄大于或等于该年龄的对象直接进入老年代。

#### 空间分配担保

在发生 Minor GC 之前，虚拟机会先检查老年代最大可用的连续空间是否大于新生代所有对象的空间总和，如果这个条件成立，那么 Minor GC 可以确保是安全的。

只要老年代的连续空间大于新生代对象总大小或者历次晋升的平均大小，就会进行 Minor GC，否则将进行 Full GC。

## Object 类的部分方法

### toString

方法定义：
```
public String toString()
```

该方法返回一个代表该对象的字符串。该方法的默认实现返回的字符串在绝大多数情况下是没有信息量的，因此通常都需要在子类中重写该方法。

### equals

方法定义：
```
public boolean equals(Object obj)
```

该方法检验两个对象是否相等。该方法的默认实现使用 == 运算符检验两个对象是否相等，通常都需要在子类中重写该方法。

### hashCode

方法定义：
```
public native int hashCode()
```

该方法返回对象的散列码。关键字 native 表示实现方法的编程语言不是 Java。

散列码是一个整数，用于在散列集合中存储并能快速查找对象。

根据散列约定，如果两个对象相同，它们的散列码一定相同，因此如果在子类中重写了 equals 方法，必须在该子类中重写 hashCode 方法，以保证两个相等的对象对应的散列码是相同的。

两个相等的对象一定具有相同的散列码，两个不同的对象也可能具有相同的散列码。实现 hashCode 方法时，应避免过多地出现两个不同的对象也可能具有相同的散列码的情况。

### finalize

方法定义：
```
protected void finalize() throws Throwable
```

该方法用于垃圾回收。如果一个对象不再能被访问，就变成了垃圾，finalize 方法会被该对象的垃圾回收程序调用。该方法的默认实现不做任何事，如果必要，子类应该重写该方法。

该方法可能抛出 Throwable 异常。

### clone

方法定义：
```
protected native Object clone() throws CloneNotSupportedException
```

该方法用于复制一个对象，创建一个有单独内存空间的新对象。

不是所有的对象都可以复制，只有当一个类实现了 java.lang.Cloneable 接口时，这个类的对象才能被复制。

该方法可能抛出 CloneNotSupportedException 异常。

### getClass

方法定义：
```
public final native Class<?> getClass()
```

该方法返回对象的元对象。元对象是一个包含类信息的对象，包括类名、构造方法和方法等。

一个类只有一个元对象。每个对象都有一个元对象，同一个类的多个对象对应的元对象相同。

## 抽象类和接口

抽象类指抽象而没有具体实例的类。接口是一种与类相似的结构，在很多方面与抽象类相近。

### 抽象类

抽象类使用关键字 abstract 修饰。抽象类和常规类一样具有数据域、方法和构造方法，但是不能用 new 操作符创建实例。

抽象类可以包含抽象方法。抽象方法使用关键字 abstract 修饰，只有方法签名而没有实现，其实现由子类提供。抽象方法都是非静态的。包含抽象方法的类必须声明为抽象类。

非抽象类不能包含抽象方法。如果一个抽象父类的子类不能实现所有的抽象方法，则该子类也必须声明为抽象类。

包含抽象方法的类必须声明为抽象类，但是抽象类可以不包含抽象方法。

### 接口

接口使用关键字 interface 定义。接口只包含可见性为 public 的常量和抽象方法，不包含变量和具体方法。

和抽象类一样，接口不能用 new 操作符创建实例。

新版本的 JDK 关于接口的规则有以下变化。

从 Java 8 开始，接口方法可以由默认实现。
从 Java 9 开始，接口内允许定义私有方法。
一个类只能继承一个父类，但对接口允许多重继承。一个接口可以继承多个接口，这样的接口称为子接口。

### 抽象类和接口的区别

- 抽象类的变量没有限制，接口只包含常量，即接口的所有变量必须是 public static final。
- 抽象类包含构造方法，子类通过构造方法链调用构造方法，接口不包含构造方法。
- 抽象类的方法没有限制，接口的方法必须是 public abstract 的实例方法（注：新版本的 JDK 关于接口的规则有变化，见上文）。
- 一个类只能继承一个父类，但是可以实现多个接口。一个接口可以继承多个接口。

### 自定义比较方法

有两个接口可以实现对象之间的排序和比较大小。

Comparable 接口是排序接口。如果一个类实现了 Comparable 接口，则该类的对象可以排序。Comparable 接口包含一个抽象方法 compareTo，实现 Comparable 接口的类需要实现该方法，定义排序的依据。

Comparator 接口是比较器接口。如果一个类本身不支持排序（即没有实现 Comparable 接口），但是又需要对该类的对象排序，则可以通过实现 Comparator 接口的方式建立比较器。Comparator 接口包含两个抽象方法 compare 和 equals，其中 compare 方法是必须在实现类中实现的，而 equals 方法在任何类中默认已经实现。

如果需要对一个数组或列表中的多个对象进行排序，则可以将对象的类定义成实现 Comparable 接口，也可以在排序时定义 Comparator 比较器。

## 基本数据类型和包装类

Java 有 8 种基本数据类型，基本数据类型不属于对象。但是在很多时候需要把对象作为参数，因此需要把基本数据类型包装成对象，对应的类称为包装类。

### 基本数据类型和包装类的对应关系

每种基本数据类型都有对应的包装类，如以下表格所示。

![](https://tva1.sinaimg.cn/large/008i3skNly1gqfr2h9atkj318g0j40u8.jpg)

包装类的名称和对应的基本数据类型相同，包装类的名称的首字母大写，Integer 和 Character 例外。

### 包装类的构造方法

可以通过包装类的构造方法创建包装对象。调用构造方法时，构造方法的参数值可以是基本数据类型的值，也可以是表示值的字符串。

包装类的构造方法都是有参数的，没有无参数构造方法。

包装类的实例都是不可变的，一旦创建了包装对象，其内部的值就不能再改变。

### 自动装箱和自动拆箱

从 JDK 1.5 开始，基本数据类型和包装类之间可以进行自动转换。
将基本数据类型的值转换为包装对象，称为装箱。将包装对象转换为基本数据类型的值，称为拆箱。

## 面向对象思想

### 类的关系

#### 关联

关联是一种描述两个类之间行为的一般二元关系。

关联中的每个类可以指定一个数字或一个数字区间，表示该关联涉及类中的多少个对象。

在 Java 代码中，关联可以用数据域和方法进行实现，一个类中的方法包含另一个类的参数。

下面的代码是关联的例子。储户在银行开账户是储户类 Depositor 和银行类 Bank 之间的关联。每个储户可以在多个银行开设账户，每个银行也可以有多个储户在该银行开设账户。

```
class Depositor {
    private List<Bank> bankList;

    public Depositor() {
        bankList = new ArrayList<Bank>();
    }

    public void addBank(Bank account) {
        bankList.add(account);
    }
}
```

```
class Bank {
    private List<Depositor> depositorList;

    public Bank() {
        depositorList = new ArrayList<Depositor>();
    }

    public void addUser(Depositor depositor) {
        depositorList.add(depositor);
    }
}
```

#### 聚集和组合

聚集是一种特殊的关联形式，表示两个对象之间的所属关系。聚集模拟具有（has-a）关系。

所有者对象称为聚集对象，对应的类称为聚集类；从属对象称为被聚集对象，对应的类称为被聚集类。

一个对象可以被几个聚集对象所拥有。如果一个对象被一个聚集对象所专有，该对象和聚集对象之间的关系就称为组合。

下面的代码是聚集和组合的例子。司机类 Driver 是聚集类，汽车类 Car 和身份证类 IDCard 是被聚集类。每个司机驾驶一辆汽车，并拥有一张身份证。由于一辆汽车可以被多个司机驾驶，因此 Driver 和 Car 之间的关系是聚集关系。由于一张身份证只能被一个人拥有，因此 Driver 和 IDCard 之间的关系是组合关系。

```
class Driver {
    private Car car;
    private IDCard idCard;
}
```

```
class Car {
}
```

```
class IDCard {
}
```

#### 依赖

依赖指两个类之间一个类使用另一个类的关系，前者称为客户（client），后者称为供应方（supplier）。

在 Java 代码中，实现依赖的方式是，客户类中的方法包含供应方类的参数。

下面的代码是依赖的例子。Java 自带的抽象类 Calendar 包含方法 setTime，该方法包含一个 Date 类型的参数，此处 Calendar 是客户类，Date 是供应方类。

```
public abstract class Calendar implements Serializable, Cloneable, Comparable<Calendar> {
    public final void setTime(Date date) {
        setTimeInMillis(date.getTime());
    }
}
```

#### 继承

继承模拟是（is-a）关系。

强是（strong is-a）关系描述两个类之间的直接继承关系，弱是（weak is-a）关系描述一个类具有某些属性。

强是关系可以用类的继承表示，弱是关系可以用接口表示。

### 类的设计原则

#### 内聚性

同一个类/模块的所有操作应该有高度关联性，支持共同的目标，只负责一项任务，即单一责任原则，称为高内聚。

不同类/模块之间的关联程度应该尽量低，对一个类/模块的修改应该尽量减少对其他类/模块的影响，称为低耦合。

#### 封装性

类中的数据域应该使用 private 修饰符隐藏其可见性，避免从外部直接访问数据域。

如果需要从外部读取数据域的值，则提供读取器方法。如果需要从外部修改数据域的值，提供设置器方法。

如果一个方法只在类的内部使用，则应该对该方法使用 private 修饰符，避免从外部调用该方法。

#### 实例和静态

依赖于类的具体实例的数据域和方法应声明为实例数据域和实例方法，反之应声明为静态数据域和静态方法。

如果一个数据域被所有实例共享，该数据域应声明为静态数据域。如果一个方法不依赖于具体实例，该方法应声明为静态方法。

#### 继承和聚集

继承模拟是（is-a）关系，聚集模拟具有（has-a）关系。应考虑两个类之间的关系为是关系还是具有关系，决定使用继承或聚集。

![](https://tva1.sinaimg.cn/large/008i3skNly1gqfrchbcfgj30ko0aodh9.jpg)

## 序列化和反序列化

把对象转换成字节序列的过程称为对象的序列化，把字节序列恢复成对象的过程称为对象的反序列化。

### 可序列化接口 Serializable

只有当一个类实现了 Serializable 接口时，这个类的实例才是可序列化的。

Serializable 接口是一个标识接口，用于标识一个对象是否可被序列化，该接口不包含任何数据域和方法。

如果试图对一个没有实现 Serializable 接口的类的实例进行序列化，会抛出 NotSerializableException 异常。

将一个对象序列化时，会将该对象的数据域进行序列化，不会对静态数据域进行序列化。

### 关键字 transient

如果一个对象的类实现了 Serializable 接口，但是包含一个不可序列化的数据域，则该对象不可序列化。为了使该对象可序列化，需要给不可序列化的数据域加上关键字 transient。

如果一个数据域可序列化，但是不想将这个数据域序列化，也可以给该数据域加上关键字 transient。

在序列化的过程中，加了关键字 transient 的数据域将被忽略。

## 反射机制

### 反射机制

Java 反射机制的核心是在程序运行时动态加载类以及获取类的信息，从而使用类和对象的数据域和方法。

### Class 类

Class 类的作用是在程序运行时保存每个对象所属的类的信息，在程序运行时分析类。一个 Class 类型的对象表示一个特定类的属性。

有三种方法可以得到 Class 类型的实例。

第一种方法是对一个对象调用 getClass 方法，获得该对象所属的类的 Class 对象。

第二种方法是调用静态方法 Class.forName，将类名作为参数，获得类名对应的 Class 对象。

第三种方法是对任意的 Java 类型 T（包括基本数据类型、引用类型、数组、关键字 void），调用 T.class 获得类型 T 对应的 Class 对象，此时获得的 Class 对象表示一个类型，但是这个类型不一定是一种类。

三种方法中，通过静态方法 Class.forName 获得 Class 对象是最常用的。

### Class 类的常用方法

Class 类中最常用的方法是 getName，该方法返回类的名字。

Class 类中的 getFields、getMethods 和 getConstructors 方法分别返回类中所有的公有（即使用可见修饰符 public 修饰）的数据域、方法和构造方法。

Class 类中的 getDeclaredFields、getDeclaredMethods 和 getDeclaredConstructors 方法分别返回类中所有的数据域、方法和构造方法（包括所有可见修饰符）。

Class 类中的 getField、getMethod 和 getConstructor 方法分别返回类中单个的公有（即使用可见修饰符 public 修饰）的数据域、方法和构造方法。

Class 类中的 getDeclaredField、getDeclaredMethod 和 getDeclaredConstructor 方法分别返回类中单个的数据域、方法和构造方法（包括所有可见修饰符）。

![](https://tva1.sinaimg.cn/large/008i3skNly1gqfrk6kwkwj319y0b40ve.jpg)

# 异常处理

## 异常处理

编程错误可以分成三类：语法错误、逻辑错误和运行错误。

语法错误（也称编译错误）是在编译过程中出现的错误，由编译器检查发现语法错误。

逻辑错误指程序的执行结果与预期不符，可以通过调试定位并发现错误的原因。

运行错误是引起程序非正常终端的错误，需要通过异常处理的方式处理运行错误。

### 异常处理概念

运行错误会引起异常，如果不对异常进行捕获和处理，程序就会非正常终止，并可能引起别的问题。

为了避免程序非正常终止，保证程序的稳定性，需要使用异常处理的功能。

Java 提供了 try-catch 块的结构，用于捕获并处理异常。该结构包括 try 块和 catch 块两部分，分别以关键字 try 和 catch 开始，catch 块包含特定异常类型的参数。在 try 块中包含可能抛出异常的语句，当 try 块中的一个语句抛出异常且和 catch 块的参数的异常类型一致时，try 块中剩下的语句会被跳过，catch 块中的语句会被执行。

### 异常类型

Java 的异常类型是 Exception 类，它是 Throwable 类的子类。

Exception 类描述由程序和外部环境引起的错误，可以通过程序捕获和处理这些异常。Exception 类有多个子类，分别描述特定的异常。

RuntimeException 类是 Exception 类的子类，描述运行时异常。RuntimeException 类有多个子类，分别描述特定的运行时异常。

### 异常处理的操作

Java 的异常处理基于三种操作：声明异常、抛出异常和捕获异常。

#### 声明异常

如果一个方法可能抛出异常，则需要在方法声明中使用关键字 throws 声明异常。如果一个方法可能抛出多种类型的异常，则需要在关键字 throws 之后依次列举可能抛出的异常类型。

#### 抛出异常

如果程序检查到错误，则可以创建一个异常的实例并抛出该异常实例。使用关键字 throw 抛出异常。

需要注意声明异常的关键字 throws 和抛出异常的关键字 throw 的区别。

#### 捕获异常

捕获异常通过 try-catch 块实现。每个 catch 块包含一个特定异常类型的参数，如果需要捕获多种异常，则需要使用多个 catch 块，每个 catch 块分别包含一个特定异常类型的参数。

如果 try 块的执行过程中没有出现异常，则跳过 catch 块。

如果 try 块中的一个语句抛出一个异常，则跳过 try 块中剩下的语句，寻找可以处理该异常的代码，处理异常的代码称为异常处理器。具体而言，依次检查每个 catch 块，寻找可以处理该异常的 catch 块。

- 如果发现一个 catch 块的参数的异常类型和抛出的异常实例匹配，则将异常实例赋给该 catch 块的参数，执行该 catch 块的语句。
- 如果在当前方法中没有发现异常处理器，则异常没有被捕获和处理，退出当前的方法，并将异常传递给当前方法的调用者，继续寻找异常处理器。

如果一个 catch 块可以捕获一个父类的异常对象，则该 catch 块也能捕获该父类的所有子类的异常对象。

由于父类包含子类，因此需要注意 catch 块的顺序，子类异常对应的 catch 块必须出现在父类异常的 catch 块之前，否则会出现编译错误。

### finally 子句

有时，无论异常是否出现或者被捕获，都需要执行一些语句，可以通过 finally 子句实现。使用关键字 finally 声明 finally 子句。

如果在 try-catch 块中包含 return 语句，finally 子句将在方法返回之前被执行。

```
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String str1 = scanner.next();
        String opStr = scanner.next();
        String str2 = scanner.next();
        scanner.close();
        System.out.println(calculate(str1, opStr, str2));
    }

    public static int calculate(String str1, String opStr, String str2) {
        int result = 0;
        try {
            int num1 = Integer.parseInt(str1);
            int num2 = Integer.parseInt(str2);
            char op = opStr.charAt(0);
            switch (op) {
            case '+':
                result = num1 + num2;
                break;
            case '-':
                result = num1 - num2;
                break;
            case '*':
                result = num1 * num2;
                break;
            case '/':
                result = num1 / num2;
                break;
            default:
                throw new RuntimeException("Invalid expression");
            }
            return result;
        } catch (NumberFormatException ex) {
            System.out.println("NumberFormatException");
        } catch (ArithmeticException ex) {
            System.out.println("ArithmeticException");
        } catch (Exception ex) {
            System.out.println(ex.getMessage());
        } finally {
            System.out.println("The finally block");
        }
        return result;
    }
}
```

上述代码的作用是，在命令行依次输入第一个数、运算符和第二个数，计算表达式的结果并输出。方法 calculate 根据三个参数计算结果，包含 try-catch 块和 finally 子句。

由于 Exception 类包含了 NumberFormatException 类和 ArithmeticException 类，因此 Exception 类的 catch 块必须放在 NumberFormatException 类和 ArithmeticException 类的 catch 块之后，否则会出现编译错误。

方法 calculate 中的 finally 子句在任何情况下都会执行。如果 try 块的执行过程中没有出现异常，则 finally 子句将在方法返回之前被执行。

# Java虚拟机

## 运行时数据区域

Java 虚拟机在执行 Java 程序的过程中会把它管理的内存划分成若干个不同的数据区域。这些区域有不同的用途。

### 程序计数器

程序计数器是一块较小的内存空间，可以看作当前线程所执行的字节码的行号指示器。字节码解释器工作时，通过改变程序计数器的值选取下一条需要执行的字节码指令，分支、循环、跳转、异常处理、线程恢复等功能都需要依赖程序计数器完成。

为了线程切换后能恢复到正确的执行位置，每个线程都需要有独立的程序计数器。由于每个线程的程序计数器是独立存储的，因此各线程之间的程序计数器互不影响，这类内存区域被称为线程私有的内存区域。

程序计数器是唯一不会出现 OutOfMemoryError 的内存区域。

### Java 虚拟机栈

和程序计数器一样，Java 虚拟机栈也是线程私有的，它的生命周期与线程相同。

虚拟机栈描述的是 Java 方法执行的内存模型，每个方法被执行的时候会创建一个栈帧，用于存储局部变量表、操作栈、动态链接、方法出口等信息。一个方法被调用直至执行完成的过程对应一个栈帧在虚拟机中从入栈到出栈的过程。

局部变量表存放编译器可知的各种基本数据类型、对象引用类型和返回地址类型。

Java 虚拟机栈会出现两种异常。

- 如果虚拟机栈不可以动态扩展，当线程请求的栈深度大于虚拟机所允许的深度时，将抛出 StackOverflowError 异常；
- 如果虚拟机栈可以动态扩展，当无法申请到足够的内存时，将抛出 OutOfMemoryError 异常。

### 本地方法栈

本地方法栈和虚拟机栈的作用相似。区别在于，虚拟机栈为虚拟机执行 Java 方法服务，本地方法栈为虚拟机使用到的本地方法服务。有的虚拟机（如 HotSpot 虚拟机）把本地方法栈和虚拟机栈合二为一。

和虚拟机栈一样，本地方法栈也会出现 StackOverflowError 和 OutOfMemoryError 两种异常。

### Java 堆

对于大多数应用而言，Java 堆是 Java 虚拟机管理的内存中最大的一块。Java 堆是被所有线程共享的内存区域，其目的是存放对象实例，几乎所有的对象实例都在堆中分配内存。

Java 堆是垃圾回收器管理的主要内存，因此也称为 GC 堆（Garbage Collected Heap）。从垃圾回收的角度，由于现代编译器基本都采用分代垃圾回收算法，所以 Java 堆还可以分成新生代和老年代，新生代又可以细分成 Eden 区、From Survivor 区、To Survivor 区等。细分成多个空间的目的是更好地回收内存或者更快地分配内存。

### 方法区

和 Java 堆一样，方法区也是被所有线程共享的内存区域。方法区用于存储已经被虚拟机加载的类信息、常量、静态变量、即时编译器编译后的代码等数据。

当方法区无法满足内存分配需求时，将抛出 OutOfMemoryError 异常。

JDK 1.8 将方法区彻底移除，取而代之的是元空间，元空间使用的是直接内存。

### 运行时常量池

运行时常量池是方法区的一部分。Class 文件中除了有类的版本、字段、方法、接口等描述信息外，还有常量池信息，用于存放编译器生成的字面量和符号引用，这些信息将在类加载后存放到方法区的运行时常量池中。

运行时常量池也受到方法区内存的限制，当常量池无法再申请到内存时将抛出 OutOfMemoryError 异常。

### 直接内存

直接内存不是虚拟机运行时数据区域的一部分，也不是虚拟机规范中定义的内存区域，但是这部分也被频繁地使用，而且也可能导致 OutOfMemoryError 异常出现。

本机直接内存的分配不受到 Java 堆大小的限制，但是直接内存仍然受到本机总内存地大小及处理器寻址空间的限制。如果各个内存区域的总和大于物理内存限制，就会导致动态扩展时出现 OutOfMemoryError 异常。

## 垃圾回收

垃圾回收，顾名思义就是释放垃圾占用的空间，从而提升程序性能，防止内存泄露。当一个对象不再被需要时，该对象就需要被回收并释放空间。

Java 内存运行时数据区域包括程序计数器、虚拟机栈、本地方法栈、堆等区域。其中，程序计数器、虚拟机栈和本地方法栈都是线程私有的，当线程结束时，这些区域的生命周期也结束了，因此不需要过多考虑回收的问题。而堆是虚拟机管理的内存中最大的一块，堆中的内存的分配和回收是动态的，垃圾回收主要关注的是堆空间。

### 调用垃圾回收器的方法

调用垃圾回收器的方法是 gc，该方法在 System 类和 Runtime 类中都存在。

在 Runtime 类中，方法 gc 是实例方法，方法 System.gc 是调用该方法的一种传统而便捷的方法。

在 System 类中，方法 gc 是静态方法，该方法会调用 Runtime 类中的 gc 方法。

其实，java.lang.System.gc 等价于 java.lang.Runtime.getRuntime.gc 的简写，都是调用垃圾回收器。

方法 gc 的作用是提示 Java 虚拟机进行垃圾回收，该方法由系统自动调用，不需要人为调用。该方法被调用之后，由 Java 虚拟机决定是立即回收还是延迟回收。

### finalize 方法

与垃圾回收有关的另一个方法是 finalize 方法。该方法在 Object 类中被定义，在释放对象占用的内存之前会调用该方法。该方法的默认实现不做任何事，如果必要，子类应该重写该方法，一般建议在该方法中释放对象持有的资源。

### 判断对象是否可回收

垃圾回收器在对堆进行回收之前，首先需要确定哪些对象是可回收的。常用的算法有两种，引用计数算法和根搜索算法。

#### 引用计数算法

引用计数算法给每个对象添加引用计数器，用于记录对象被引用的计数，引用计数为 0 的对象即为可回收的对象。

虽然引用计数算法的实现简单，判定效率也很高，但是引用计数算法无法解决对象之间循环引用的情况。如果多个对象之间存在循环引用，则这些对象的引用计数永远不为 0，无法被回收。因此 Java 语言没有使用引用计数算法。

#### 根搜索算法

主流的商用程序语言都是使用根搜索算法判断对象是否可回收。根搜索算法的思路是，从若干被称为 GC Roots 的对象开始进行搜索，不能到达的对象即为可回收的对象。

在 Java 中，GC Roots 一般包含下面几种对象：

- 虚拟机栈中引用的对象；
- 本地方法栈中的本地方法引用的对象；
- 方法区中的类静态属性引用的对象；
- 方法区中的常量引用的对象。

#### 引用的分类

引用计数算法和根搜索算法都需要通过判断引用的方式判断对象是否可回收。

在 JDK 1.2 之后，Java 将引用分成四种，按照引用强度从高到低的顺序依次是：强引用、软引用、弱引用、虚引用。

- 强引用是指在程序代码中普遍存在的引用。垃圾回收器永远不会回收被强引用关联的对象。
- 软引用描述还有用但并非必需的对象。只有在系统将要发生内存溢出异常时，被软引用关联的对象才会被回收。在 JDK 1.2 之后，提供了 SoftReference 类实现软引用。
- 弱引用描述非必需的对象，其强度低于软引用。被弱引用关联的对象只能存活到下一次垃圾回收发生之前，当垃圾回收器工作时，被弱引用关联的对象一定会被回收。在 JDK 1.2 之后，提供了 WeakReference 类实现弱引用。
- 虚引用是最弱的引用关系。一个对象是否有虚引用的存在，完全不会对其生存时间构成影响，也无法通过虚引用取得一个对象实例。为一个对象设置虚引用关联的唯一目的就是能在这个对象被回收时收到一个系统通知。在 JDK 1.2 之后，提供了 PhantomReference 类实现虚引用。

### 垃圾回收算法

#### 标记—清除算法

标记—清除算法是最基础的垃圾回收算法，后续的垃圾收集算法都是基于标记—清除算法进行改进而得到的。标记—清除算法分为“标记”和“清除”两个阶段，首先标记出所有需要回收的对象，在标记完成后统一回收所有被标记的对象。

标记—清除算法有两个主要缺点。一是效率问题，标记和清除的效率都不高，二是空间问题，标记清除之后会产生大量不连续的内存碎片，导致程序在之后的运行过程中无法为较大对象找到足够的连续内存。

#### 复制算法

复制算法是将可用内存分成大小相等的两块，每次只使用其中的一块，当用完一块内存时，将还存活着的对象复制到另外一块内存，然后把已使用过的内存空间一次清理掉。

复制算法解决了效率问题。由于每次都是对整个半区进行内存回收，因此在内存分配时不需要考虑内存碎片等复杂情况，只要移动堆顶指针，按顺序分配内存即可。复制算法的优点是实现简单，运行高效，缺点是将内存缩小为了原来的一半，以及在对象存活率较高时复制操作的次数较多，导致效率降低。

#### 标记—整理算法

标记—整理算法是根据老年代的特点提出的。标记过程与标记—清除算法一样，但后续步骤不是直接回收被标记的对象，而是让所有存活的对象都向一端移动，然后清除边界以外的内存。

#### 分代收集算法

分代收集算法根据对象的存活周期不同将内存划分为多个区域，对每个区域选用不同的垃圾回收算法。

一般把 Java 堆分为新生代和老年代。在新生代中，大多数对象的生命周期都很短，因此选用复制算法。在老年代中，对象存活率高，因此选用标记—清除算法或标记—整理算法。

### 分配内存与回收策略

Java 堆可以分成新生代和老年代，新生代又可以细分成 Eden 区、From Survivor 区、To Survivor 区等。对于不同的对象，有相应的内存分配规则。

#### Minor GC 和 Full GC

Minor GC 指发生在新生代的垃圾回收操作。因为大多数对象的生命周期都很短，因此 Minor GC 会频繁执行，一般回收速度也比较快。

Full GC 也称 Major GC，指发生在老年代的垃圾回收操作。出现了 Full GC，经常会伴随至少一次的 Minor GC。老年代对象的存活时间长，因此 Full GC 很少执行，而且执行速度会比 Minor GC 慢很多。

#### 对象优先在 Eden 区分配

大多数情况下，对象在新生代 Eden 区分配，当 Eden 区空间不够时，发起 Minor GC。

#### 大对象直接进入老年代

大对象是指需要连续内存空间的对象，最典型的大对象是那种很长的字符串以及数组。大对象对于虚拟机的内存分配而言是坏消息，经常出现大对象会导致内存还有不少空间时就提前触发垃圾回收以获取足够的连续空间分配给大对象。

将大对象直接在老年代中分配的目的是避免在 Eden 区和 Survivor 区之间出现大量内存复制。

#### 长期存活的对象进入老年代

虚拟机采用分代收集的思想管理内存，因此需要识别每个对象应该放在新生代还是老年代。虚拟机给每个对象定义了年龄计数器，对象在 Eden 区出生之后，如果经过第一次 Minor GC 之后仍然存活，将进入 Survivor 区，同时对象年龄变为 1，对象在 Survivor 区每经过一次 Minor GC 且存活，年龄就增加 1，增加到一定阈值时则进入老年代（阈值默认为 15）。

#### 动态对象年龄判定

为了能更好地适应不同程序的内存状况，虚拟机并不总是要求对象的年龄必须达到阈值才能进入老年代。如果在 Survivor 区中相同年龄的所有对象的空间总和大于 Survivor 区空间的一半，则年龄大于或等于该年龄的对象直接进入老年代。

#### 空间分配担保

在发生 Minor GC 之前，虚拟机会先检查老年代最大可用的连续空间是否大于新生代所有对象的空间总和，如果这个条件成立，那么 Minor GC 可以确保是安全的。

只要老年代的连续空间大于新生代对象总大小或者历次晋升的平均大小，就会进行 Minor GC，否则将进行 Full GC。

# 多线程

## 1.进程和线程

程序是含有指令和数据的文件，是静态的代码，被存储在磁盘或其他的数据存储设备中。进程是程序的一次执行过程，线程是进程划分成的更小的运行单位。

### 进程和线程的联系和区别

进程是程序的一次执行过程，是系统运行程序的基本单位，因此进程是动态的。系统运行一个程序即为一个进程的创建、运行以及消亡的过程。

线程是比进程更小的执行单位。一个进程在其执行的过程中可以产生多个线程，多个线程共享进程的堆和方法区内存资源，每个线程都有自己的程序计数器、虚拟机栈和本地方法栈。由于线程共享进程的内存，因此系统产生一个线程或者在多个线程之间切换工作时的负担比进程小得多，线程也称为轻量级进程。

进程和线程最大的区别是，各进程是独立的，而各线程则不一定独立，因为同一进程中的多个线程极有可能会相互影响。线程执行开销小，但不利于资源的管理和保护，进程则相反。

### 线程的状态

线程在运行的生命周期中的任何时刻只能是 6 种不同状态的其中一种。

- 初始状态（NEW）：线程已经构建，尚未启动。
- 运行状态（RUNNABLE）：包括就绪（READY）和运行中（RUNNING）两种状态，统称为运行状态。
- 阻塞状态（BLOCKED）：线程被锁阻塞。
- 等待状态（WAITING）：线程需要等待其他线程做出特定动作（通知或中断）。
- 等待状态（WAITING）：线程需要等待其他线程做出特定动作（通知或中断）。
- 终止状态（TERMINATED）：当前线程已经执行完毕。

### 多线程的优点和可能存在的问题

线程也称为轻量级进程，是程序执行的最小单位，线程间的切换和调度的成本远远小于进程，多个线程同时运行可以减少线程上下文切换的开销。多线程是开发高并发系统的基础，利用好多线程机制可以显著提高系统的并发能力和性能。

多线程并发编程并不总是能提高程序的执行效率和运行速度，而且可能存在一些问题，包括内存泄漏、上下文切换、死锁以及受限于硬件和软件的资源限制问题等。

## 2.关键字synchronized和volatile

关键字 synchronized 和 volatile 是多线程中经常用到的两个关键字。

### 关键字 synchronized

关键字 synchronized 解决的是多个线程之间访问资源的同步性，该关键字可以保证被它修饰的方法或者代码块在任意时刻只能有一个线程执行。

关键字 synchronized 最主要的三种使用方式是：修饰实例方法、修饰静态方法、修饰代码块。

- 修饰实例方法：给当前对象实例加锁，进入同步代码之前需要获得当前对象实例的锁。
- 修饰静态方法：给当前类加锁，进入同步代码之前需要获得当前类的锁。
- 修饰代码块：指定加锁对象，给指定对象加锁，进入同步代码块之前需要获得指定对象的锁。

### 关键字 volatile

关键字 volatile 解决的是变量在多个线程之间的可见性，该关键字修饰的变量会直接在主内存中进行读写操作，保证了变量的可见性。

除了保证变量的可见性以外，关键字 volatile 还有一个作用是确保代码的执行顺序不变。为了提高执行程序时的性能，编译器和处理器会对指令进行重排序优化，因此代码的执行顺序和编写代码的顺序可能不一致。添加关键字 volatile 可以禁止指令进行重排序优化。

关键字 volatile 解决的是变量在多个线程之间的可见性，该关键字修饰的变量会直接在主内存中进行读写操作，保证了变量的可见性。

除了保证变量的可见性以外，关键字 volatile 还有一个作用是确保代码的执行顺序不变。为了提高执行程序时的性能，编译器和处理器会对指令进行重排序优化，因此代码的执行顺序和编写代码的顺序可能不一致。添加关键字 volatile 可以禁止指令进行重排序优化。

只有当一个变量满足以下两个条件时，才能使用关键字 volatile。

- 对变量的写入操作不依赖变量的当前值，或者能确保只有单个线程更新变量的值。
- 该变量没有包含在具有其他变量的不变式中。

### 关键字 synchronized 和 volatile 的区别

- 关键字 volatile 是线程同步的轻量级实现，不需要加锁，因此性能优于关键字 synchronized。
- 关键字 synchronized 可以修饰方法和代码块，关键字 volatile 只能修饰变量。
- 关键字 synchronized 可能发生阻塞，关键字 volatile 不会发生阻塞。
- 关键字 synchronized 可以保证数据的可见性和原子性，关键字 volatile 只能保证数据的可见性，不能保证数据的原子性。
- 关键字 synchronized 解决的是多个线程之间访问资源的同步性，关键字 volatile 解决的是变量在多个线程之间的可见性。

## 3.多线程相关的方法

### Thread 类的方法

#### run 和 start

方法 run 在 Runnable 接口中被定义，方法 start 在 Thread 类中被定义。

创建一个 Thread 类的实例，即为创建了一个处于初始状态的线程。对一个处于初始状态的线程调用方法 start，该线程被启动，进入运行状态。调用方法 start 之后，方法 run 会自动执行。

通过调用方法 start，执行方法 run，才是多线程工作。如果直接执行方法 run，则方法 run 会被当成一个主线程下的普通方法执行，而不会在某个线程中执行，因此不是多线程工作。

#### sleep

方法 sleep 在 Thread 类中被定义。该方法的作用是使当前线程暂停执行一段时间，让其他线程有机会继续执行，但是该方法不会释放锁。

方法 sleep 需要捕获 InterruptedException 异常。

#### join

方法 join 在 Thread 类中被定义。该方法的作用是阻塞调用该方法的线程，直到当前线程执行完毕之后，调用该方法的线程再继续执行。

方法 join 需要捕获 InterruptedException 异常。

#### yield

方法 yield 在 Thread 类中被定义。该方法的作用是暂停当前正在执行的线程对象，并执行其他线程。实际调用方法 yield 时无法保证一定能让其他线程执行，因为线程调度时可能再次选中原来的线程对象。

### Object 类的方法

#### wait

方法 wait 在 Object 类中被定义。该方法必须在 synchronized 语句块内使用，作用是释放锁，让其他线程可以运行，当前线程进入等待池中。

#### notify 和 notifyAll

方法 notify 和 notifyAll 在 Object 类中被定义。

方法 notify 的作用是从等待池中移走任意一个等待当前对象的线程并放到锁池中，只有锁池中的线程可以获取锁。

方法 notifyAll 的作用是从等待池中移走全部等待当前对象的线程并放到锁池中，锁池中的这些线程将争夺锁。

#### 中断线程

中断线程的方法是 interrupt，在 Thread 类中被定义。该方法不会中断一个正在运行的线程，只是改变中断标记。

当线程处于等待状态、超时等待状态或阻塞状态时，如果对线程调用方法 interrupt 将线程的中断标记设为 true，则中断标记会被清除，同时会抛出 InterruptedException 异常。可以通过 try-catch 块捕获该异常，即可终止线程。

当线程处于运行状态时，可以对线程调用方法 interrupt 将线程的中断标记设为 true，从而达到终止线程的目的，也可以添加一个 volatile 修饰的额外标记，当需要终止线程时，更改该标记的值即可。

不推荐使用方法 stop 和 destroy 终止线程。

- 方法 stop 会立即停止方法 run 中剩余的全部工作，并抛出 ThreadDeath 错误，导致清理性工作无法完成，另外方法 stop 会立即释放该线程的所有锁，导致对象状态不一致。
- 方法 destroy 只是抛出 NoSuchMethodError，没有做任何事情，因此无法终止线程。

## 4.线程池

线程池是一种线程的使用模式。创建若干个可执行的线程放入一个池（容器）中，有任务需要处理时，会提交到线程池中的任务队列，处理完之后线程并不会被销毁，而是仍然在线程池中等待下一个任务。

### 线程池的好处

在开发过程中，合理地使用线程池可以带来 3 个好处。

- 降低资源消耗。重复利用线程池中已经创建的线程，可以避免频繁地创建和销毁线程，从而减少资源消耗。
- 降低资源消耗。重复利用线程池中已经创建的线程，可以避免频繁地创建和销毁线程，从而减少资源消耗。
- 提高线程的可管理性。线程是稀缺资源，如果无限制地创建，不仅会消耗系统资源，还会降低系统的稳定性，使用线程池可以进行统一分配、调优和监控。

### 线程池的创建

可以通过 ThreadPoolExecutor 类创建线程池。ThreadPoolExecutor 类有 4 个构造方法，其中最一般化的构造方法包含 7 个参数。

```
public ThreadPoolExecutor(int corePoolSize, int maximumPoolSize, long keepAliveTime, TimeUnit unit, BlockingQueue<Runnable> workQueue, ThreadFactory threadFactory, RejectedExecutionHandler handler)
```

7 个参数的含义如下:

- corePoolSize: 核心线程数，定义了最少可以同时运行的线程数量，当有新的任务时就会创建一个线程执行任务，当线程池中的线程数量达到 corePoolSize 之后，到达的任务进入阻塞队列。
- maximumPoolSize: 最大线程数，定义了线程池中最多能创建的线程数量。
- keepAliveTime: 等待时间，当线程池中的线程数量大于 corePoolSize 时，如果一个线程的空闲时间达到 keepAliveTime 时则会终止，直到线程池中的线程数不超过 corePoolSize。
- unit: 参数 keepAliveTime 的单位。
- workQueue: 阻塞队列，用来存储等待执行的任务。
- threadFactory: 创建线程的工厂。
- handler: 当拒绝处理任务时的策略。

### 向线程池提交任务

可以通过方法 execute 向线程池提交任务。该方法被调用时，线程池会做如下操作。

1. 如果正在运行的线程数量小于 corePoolSize，则创建核心线程运行这个任务。
2. 如果正在运行的线程数量大于或等于 corePoolSize，则将这个任务放入阻塞队列。
3. 如果阻塞队列满了，而且正在运行的线程数量小于 maximumPoolSize，则创建非核心线程运行这个任务。
4. 如果阻塞队列满了，而且正在运行的线程数量大于或等于 maximumPoolSize，则线程池抛出 RejectExecutionException 异常。

上述操作中提到了两个概念，「核心线程」和「非核心线程」。核心线程和非核心线程的最大数目在创建线程池时被指定。核心线程和非核心线程的区别如下。

- 向线程池提交任务时，首先创建核心线程运行任务，直到核心线程数到达上限，然后将任务放入阻塞队列。
- 只有在核心线程数到达上限，且阻塞队列满的情况下，才会创建非核心线程运行任务。

### 关闭线程池

可以通过调用线程池的方法 shutdown 或 shutdownNow 关闭线程池。这两个方法的原理是遍历线程池中的工作线程，对每个工作线程调用 interrupt 方法中断线程，无法响应中断的任务可能永远无法终止。

方法 shutDown 和 shutDownNow 有以下区别。

- 方法 shutDown 将线程池的状态设置成 SHUTDOWN，正在执行的任务继续执行，没有执行的任务将中断。
- 方法 shutDownNow 将线程池的状态设置成 STOP，正在执行的任务被停止，没有执行的任务被返回。

# 容器

## 1.Iterable 接口和 Iterator 接口

Iterable 接口从 JDK 1.5 开始出现，是 Java 容器的最顶级的接口之一，该接口的作用是使容器具备迭代元素的功能。

Iterator 接口从 JDK 1.2 开始出现，其含义是迭代器，可以用于迭代容器中的元素。

### Iterable 接口的方法

#### iterator

方法 iterator 是 Iterable 接口的核心方法，返回 Iterator 类的迭代器实例。

#### forEach

方法 forEach 从 JDK 1.8 开始出现。该方法有默认实现，其作用是对容器中的每个元素进行处理。

#### spliterator

方法 spliterator 从 JDK 1.8 开始出现。该方法有默认实现，其作用是并行遍历元素。

### Iterator 接口的方法

#### hasNext

方法 hasNext 的作用是检测容器中是否还有需要迭代的元素。

#### next

方法 next 的作用是返回迭代器指向的元素，并且更新迭代器的状态，将迭代器指向的元素后移一位。

#### remove

方法 remove 的作用是将迭代器指向的元素删除。该方法有默认实现，默认实现为抛出 UnsupportedOperationException 异常，如果迭代器迭代的容器不支持 remove 操作，则对迭代器调用方法 remove 时会抛出 UnsupportedOperationException 异常。

#### forEachRemaining

方法 forEachRemaining 从 JDK 1.8 开始出现。该方法有默认实现，其作用是对容器中的剩余元素进行处理，直到剩余元素处理完毕或者抛出异常。

## 2.Collection接口

Collection 接口统一定义了单列容器，该接口继承了 Iterable 接口。

### Collection接口的常用方法

#### 添加元素

添加元素的方法有 add 和 addAll，其中 add 一次添加一个元素，addAll 一次将另一个容器中的元素全部添加到当前容器中。

方法 addAll 和集合的并集运算相似。

#### 删除元素

删除元素的方法有 remove、removeAll 和 clear，其中 remove 一次删除一个元素，removeAll 一次将另一个容器中的元素全部从当前容器中删除，clear 删除当前容器中的全部元素。

方法 removeAll 和集合的差集运算相似。

#### 保留元素

保留元素的方法有 retainAll，该方法保留既在当前容器中又在另一个容器中的元素，和集合的交集运算相似。

#### 判断包含元素

判断包含元素的方法有 contains 和 containsAll，其中 contains 判断当前容器是否包含一个指定元素，containsAll 判断当前容器是否包含另一个容器中的全部元素。

#### 其他方法

方法 isEmpty 判断当前容器是否为空（即不包含元素），方法 size 返回容器中的元素数目，方法 toArray 将容器转化成 Object 数组并返回。

### Collection接口和其他容器类的关系

List 和 Set 是 Collection 接口的子接口。

- List 是线性表，存储一组顺序排列的元素。
- Set 是集合，存储一组互不相同的元素。

另一个描述容器的接口是 Map，该接口与 Collection 并列存在。不同于 Collection 接口存放单值元素，Map 接口存放的是键值对。

## 3.线性表

List 接口定义线性表，该接口继承了 Collection 接口。List 接口的实现类有 ArrayList、LinkedList 和 Vector。

### List 接口的常用方法

由于 List 接口继承了 Collection 接口，因此 List 接口支持 Collection 接口的一切方法。List 接口还支持通过下标访问元素，根据下标进行添加和删除元素的操作，以及可以生成双向遍历线性表的新迭代器。

以下列举的方法是 List 接口中新定义的方法（和 Collection 相比新定义的方法）。

#### 添加元素

添加元素的方法有 add 和 addAll，其中 add 一次添加一个元素，addAll 一次将另一个容器中的元素全部添加到当前线性表中。这两个方法都可以指定下标，在指定下标处添加元素。

#### 删除元素

删除元素的方法有 remove，可以指定下标，删除指定下标处的元素。

#### 修改元素

修改元素的方法有 set，将指定下标处的元素修改成新的元素。

#### 获得元素以及获得元素下标

获得元素的方法有 get，返回指定下标处的元素。

获得元素下标的方法有 indexOf 和 lastIndexOf，分别返回第一个匹配元素的下标和最后一个匹配元素的下标。

#### 获得子线性表

获得子线性表的方法有 subList，返回指定下标范围的子线性表。

#### 生成线性表迭代器

生成线性表迭代器的方法有 listIterator，该方法如果没有参数则返回线性表中元素的迭代器，如果指定下标则返回从指定下标开始的元素的迭代器。线性表迭代器的接口是 ListIterator，该接口继承了 Iterator 接口，支持双向遍历。

### 数组线性表类 ArrayList 和链表类 LinkedList

ArrayList 类和 LinkedList 类是 List 接口的两个实现类，底层实现分别是数组和双向链表。

随机访问元素方面：ArrayList 类的底层实现是数组，因此可以快速返回指定下标处的元素；LinkedList 类的底层实现是双向链表，因此需要遍历元素才能得到指定下标处的元素。

插入和删除元素方面：ArrayList 进行插入和删除元素时，除了在尾部插入和删除元素不需要移动其他元素，否则都需要移动其他元素；LinkedList 进行插入和删除元素时，只需要对插入位置前后的元素的前驱和后继信息进行修改即可，因此在头部和尾部插入和删除元素可以快速完成，在指定位置插入和删除元素时则需要首先遍历元素到指定位置。

ArrayList 类和 LinkedList 类都是不同步的，不保证线程安全。

### 向量类 Vector

Vector 类和 ArrayList 类的方法基本是相同的，主要区别是 Vector 类的所有方法都是同步的，因此可以保证线程安全。

虽然 Vector 是线程安全的，但是同步操作会花费更多的时间。在不需要保证线程安全的情况下，使用 ArrayList 比使用 Vector 效率更高。

## 4.映射和集合

Map 接口定义映射，存储一组键值对的映射关系。

Set 接口定义集合，存储一组互不相同的元素，该接口继承了 Collection 接口。

### Map 接口的概念和常用方法

Map 接口存储一组键值对的映射关系，映射中的每个键对应一个值。映射中不能有重复的键，否则会出现一个键对应多个值的情况，这违背了映射的定义。

#### 放置键值对

放置键值对的方法有 put 和 putAll，其中 put 一次放置一个键值对，putAll 一次将另一个映射中的键值对全部添加到当前映射中。在映射中放置键值对时，如果映射中没有对应的键，则在映射中新建一个键值对，否则用新的键值对覆盖原来的相同键的键值对。

#### 删除键值对

删除键值对的方法有 remove 和 clear，其中 remove 删除指定键的键值对，clear 删除当前映射中的全部键值对。

#### 判断包含键或值

判断包含键或值的方法有 containsKey 和 containsValue，其中 containsKey 判断映射中是否包含指定的键，containsValue判断映射中是否包含指定的值。

#### 根据键获得值

根据键获得值得方法有 get，该方法返回映射中指定键的值。

#### 获得键或键值对的集合

获得键或键值对的集合的方法有 entrySet 和 keySet，其中 entrySet 返回映射的所有键值对的集合，keySet 返回映射的所有键的集合。

#### 获得值的容器

获得值的容器的方法有 values，该方法返回映射的所有值的容器。

#### 其他方法

方法 isEmpty 判断当前映射是否为空（即不包含键值对），方法 size 返回映射中的键值对数目。

### Map 接口的实现类 HashMap、Hashtable 和 TreeMap

#### HashMap 和 Hashtable

HashMap 类是散列映射，通过散列函数计算键对应的存储位置，因此可以快速地完成放置键值对、删除键值对、根据键获得值的操作。

JDK 1.8 之前的 HashMap 的底层通过数组和链表实现，如果出现冲突则通过拉链法解决冲突。JDK 1.8 在解决冲突时的实现有较大变化，当链表长度大于阈值（默认为 8）时，将链表转化为红黑树，以减少搜索时间。

Hashtable 类是散列表，其功能和 HashMap 相似。以下是 HashMap 和 Hashtable 的部分区别。

- HashMap 不是线程安全的，Hashtable 的大多数方法用关键字 synchronized 修饰，因此 Hashtable 是线程安全的。
- 在不需要保证线程安全的情况下，HashMap 的效率高于 Hashtable。
- HashMap 允许键或值为 null，只能有一个键为 null，可以有一个或多个键对应的值为 null，Hashtable 不允许键或值为 null。
- 从 JDK 1.8 开始，HashMap 在链表长度大于阈值（默认为 8）时，将链表转化为红黑树以减少搜索时间，Hashtable 没有这样的机制。

#### TreeMap

TreeMap 是有序映射，键可以使用 Comparable 接口或 Comparator 接口排序。

TreeMap 的底层实现是红黑树，通过红黑树维护映射的有序性。由于要维护映射的有序性，因此 TreeMap 的各项操作的平均效率低于 HashMap，但是 TreeMap 可以按照顺序获得键值对。

### Set 接口的定义和常用方法

Set 接口存储一组互不相同的元素，一个集合中不存在两个相等的元素。

Set 接口继承了 Collection 接口，没有引入新的方法或常量，只是规定其实例不能包含相等的元素。

### Set 接口的实现类 HashSet 和 TreeSet

#### HashSet

HashSet 类是散列集合，其底层实现基于 HashMap。当对象加入散列集合时，需要判断元素是否重复，首先通过方法 hashCode 计算对象的散列码检查是否有对象具有相同的散列码，如果没有相同的散列码则没有重复元素，否则再通过方法 equals 检查是否有相等的对象。

根据散列约定，如果两个对象相同，它们的散列码一定相同，因此如果在子类中重写了 equals 方法，必须在该子类中重写 hashCode 方法，以保证两个相等的对象对应的散列码是相同的。