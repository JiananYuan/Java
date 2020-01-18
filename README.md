# Java


## Chapter 1 Java语言概述

1.1 Java语言的诞生和发展

1.2 Java语言的特点：
简单易学（去掉了指针、联合体、结构体），面向对象（封装、单一继承、多态），平台无关性，分布式，可靠性，安全性，支持多线程，支持网络编程，编译与解释共存

1.3 Java技术简介：
Java SE，Java ME，Java EE

1.4 Java虚拟机：
Java程序-----（编译）字节码-----（解释）本地机器码

1.5 Java程序种类和结构：Application，Applet，主类是Java程序执行的入口点

## Chapter 2 Java语言开发环境

2.1 Java开发工具（JDK）

2.2 Java 帮助文档

2.3 JDK的使用

## Chapter 3 Java语言基础

3.1 数据类型：基本数据类型和引用数据类型

3.2 关键字和标识符

编码习惯：类名首字母大写、变量、方法及对象首字母小写、对于标识符，大写中间单词的首字母、对于常量，大写所有字母、包名全部小写

3.3 常量

3.4 变量

3.5 数据类型转换

字符串型数据与数值数据相互转换：

Float.parseFloat(String s) // double c = Double.parseDouble("1287.233);

数值型数据转换为字符串：

string = "" + 12.65;

数据输入方式1

	import java.io.*;

	public class Main {
	    public static void main(String[] args) throws IOException {
	        String str;
	        BufferedReader buf = new BufferedReader(new InputStreamReader(System.in));
	        str = buf.readLine();
	        System.out.println(str);
	    }
	}

数据输入方式2

Scanner...

3.6 由键盘输入数据

3.7 运算符与表达式

## Chapter 4 流程控制

<br>

## Chapter 5 数组与字符串

5.1 数组的基本概念

在堆中创建了一个数组或对象之后，同时还在栈中定义了一个特殊的变量，让栈中的这个变量的取值等于数组或对象在堆内存中的首地址，栈中的这个变量成了数组或变量的引用变量（句柄）

5.2 一维数组

内置方法：

public static int binarySearch(X[] a,X key)

public static void sort(X[] a)

public static void sort(X[] a,int fromIndex,int toIndex)

public static X[] copyof( X[] original,int newLength)

public static boolean equals(X[] a,X[] a2)

for-each 语法

杨辉三角：

	import java.util.Scanner;

	public class Main {
	    private static Scanner in;
	    private static int[][] a;
	    public static void main(String[] args) {
	        in = new Scanner(System.in);
	        a = new int[11][11];
	        a[1][1] = 1;
	        for(int i = 2;i <= 10;i++) {
	            for(int j=1;j <= i;j++) {
	                a[i][j] = a[i-1][j-1] + a[i-1][j];
	            }
	        }
	        for(int i=1;i<=10;i++) {
	            for(int j=1;j<=i;j++) {
	                System.out.print(a[i][j] + " ");
	            }
	            System.out.println();
	        }
	    }
	}

5.3 多维数组

5.4 三维以上多维数组

5.5 字符串

方法：

public int length()

public boolean equals (Object anObject)

public String substring(int beginIndex)

public String substring(int beginIndex,int endIndex)

public char charAt(int index)

public int indexOf(String str)

public int compareTo(String anotherString)

public String replace(char oldChar,char newChar)

public String trim()

public String toLowerCase()

public String toUpperCase()

## Chapter 6，7，8 面向对象

6.1 类的基本概念

6.2 定义类

6.3 对象的创建与使用

6.4 参数的传递

6.5 匿名对象

7.1 类的私有成员和公有成员

注：缺省访问标识符：若在类成员的前面不加任何访问控制符，表示这个成员只能被同一个包（类库）中的类访问和调用。

7.2 方法的重载

7.3 构造方法

7.4 静态成员

7.5 对象的应用

对象赋值之后，当参数是基本参数类型的时候，则是传值方式调用；而当参数是引用变量时，则是传址方式调用。

8.1 类的继承（单继承）

Object类

equals() 

toString()

instanceof

	class Person {
	    protected String name;
	    protected int age;
	    public Person(String name,int age) {
	        this.name = name;
	        this.age = age;
	    }
	    protected void show() {
	        System.out.println("姓名：" + name + "年龄：" + age);
	    }
	}
	
	class Student extends Person {
	    private String department;
	    public Student(String name,int age,String dep) {
	        super(name,age);
	        department = dep;
	    }
	    protected void show() {
	        System.out.println("系别：" + department);
	    }
	}
	
	public class Main {
	    public static void main(String[] args) {
	        Student stu  = new Student("JiananYuan",20,"CSSE");
	        stu.show();
	    }
	}

8.2 抽象类

	import com.sun.org.apache.regexp.internal.REDebugCompiler;

	abstract class Shape {
	    protected String name;
	    public Shape(String xm) {
	        name = xm;
	        System.out.println("姓名：" + name);
	    }
	    abstract public double getArea();
	    abstract public double getLength();
	}
	
	class Circle extends Shape {
	    private final double PI = 3.14;
	    private double radius;
	    public Circle(String name,double r) {
	        super(name);
	        radius = r;
	    }
	    public double getArea() {
	        return PI * radius * radius;
	    }
	    public double getLength() {
	        return 2 * PI * radius;
	    }
	}
	
	class Rectangle extends Shape {
	    private double width,height;
	    public Rectangle(String name,double width,double height) {
	        super(name);
	        this.width = width;
	        this.height = height;
	    }
	    public double getArea() {
	        return width * height;
	    }
	    public double getLength() {
	        return 2 * (width + height);
	    }
	}
	
	public class Main {
	    public static void main(String[] args) {
	        Shape rect = new Rectangle("长方形",6.5,10.3);
	        System.out.println(";面积: " + rect.getArea());
	        System.out.println(";周长: " + rect.getLength());
	        Shape circle = new Circle("长方形",10.2);
	        System.out.println(";面积: " + circle.getArea());
	        System.out.println(";周长: " + circle.getLength());
	    }
	}

8.3 接口


