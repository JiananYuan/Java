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

接口数据成员都是静态的且必须初始化，方法必须全部是abstract的

不能多继承，但可多接口

8.4 内部类

	class Group {
	    private int age;
	    public class Student {
	        String name;
	        public Student(String n,int a) {
	            name = n;
	            age = a;
	        }
	        public void output() {
	            System.out.println("姓名：" + this.name + "；年龄：" + age);
	        }
	    }
	    public void output() {
	        Student stu = new Student("QAQ",24);
	        stu.output();
	    }
	    public static void main(String[] args) {
	        Group g = new Group();
	        g.output();
	    }
	}

------

	public class Main {
	    public static void main(String[] args) {
	        (
	                new Inner() {
	                    void setName(String n) {
	                        name = n;
	                        System.out.println(name);
	                    }
	                }
	                ).setName("Li Hua");
	    }
	    static class Inner {
	        String name;
	    }
	}

8.5 包

	import sun.util.resources.cldr.aa.CalendarData_aa_ER;

	import java.util.Calendar;
	import java.util.Random;
	
	public class Main {
	    public static void main(String[] args) {
	        Calendar today = Calendar.getInstance();
	        int y = today.get(Calendar.YEAR);
	        int m = today.get(Calendar.MONTH);
	        int d = today.get(Calendar.DATE);
	        System.out.println("今天是" + y + "年" + (m+1) + "月" + d + "日");
	        System.out.println((new Random()).nextFloat());
	    }
	}

8.6 Java语言的垃圾回收


## Chapter 9 异常处理

9.1 异常处理的基本概念

9.2 异常处理类

![异常类](https://www.png8.com/imgs/2020/01/e3e267d099493e48.png)


9.3 异常的处理

基本格式：try - catch - finally

	import jdk.nashorn.internal.runtime.arrays.ArrayIndex;

	public class Main {
	    public static void main(String[] agrs) {
	        int i;
	        int[] a = {1,2,3,4};
	        for(i=0;i<5;i++) {
	            try {
	                System.out.println(a[i]/i);
	            }
	            catch(ArrayIndexOutOfBoundsException e) {
	                System.out.println("捕获到了数组下标越界异常");
	            }
	            catch(ArithmeticException e) {
	                System.out.println("异常类名称是：" + e);
	            }
	            catch(Exception e) {
	                System.out.println("捕获" + e.getMessage() + "异常!");
	            }
	            finally {
	                System.exit(1);
	            }
	        }
	        System.out.println("继续...");
	    }
	}


9.4 抛出异常

1. 抛出异常的方法与调用方法处理异常

例子1

	public class Main {
	    public static void main(String[] args) {
	        int a = 5, b = 0;
	        try {
	            if(b == 0) {
	                throw new ArithmeticException();
	            } else {
	                System.out.println(a/b);
	            }
	        } catch(ArithmeticException e) {
	            System.out.println(e);
	            e.printStackTrace();
	        }
	    }
	}

例子2

	import java.text.NumberFormat;
	import java.util.jar.JarOutputStream;
	
	public class Main {
	    public static double multi(int n) {
	        if(n < 0) throw new IllegalArgumentException("求负数阶乘异常");
	        double s = 1;
	        for(int i=1;i<=n;i++) s *= i;
	        return s;
	    }
	    public static void main(String[] agrs) {
	        try {
	            int m = Integer.parseInt(agrs[0]);
	            System.out.println(multi(m));
	        } catch(ArrayIndexOutOfBoundsException e) {
	            System.out.println("命令行没有提供参数");
	        } catch(NumberFormatException e) {
	            System.out.println("应该输入一个整数");
	        } catch(IllegalArgumentException e) {
	            System.out.println(e.toString());
	        } finally {
	            System.out.println("end");
	        }
	    }
	}

例子3

	import java.text.NumberFormat;

	public class Main {
	    static void check(String str1) throws NullPointerException {
	        if(str1.length() > 2) {
	            str1 = null;
	            System.out.println(str1.length());
	        }
	        char ch;
	        for(int i=0;i<str1.length();i++) {
	            ch = str1.charAt(i);
	            if(!Character.isDigit(ch)) {
	                throw new NumberFormatException();
	            }
	        }
	    }
	
	    public static void main(String[] agrs) throws Exception {
	        int num;
	        try {
	            check(agrs[0]);
	            num = Integer.parseInt(agrs[0]);
	            if(num > 60) {
	                System.out.println("pass");
	            } else {
	                System.out.println("failed");
	            }
	        } catch(NullPointerException e) {
	            System.out.println("null pointer exception occurred");
	        } catch(NumberFormatException e) {
	            System.out.println("format of data wrong");
	        } catch(Exception e) {
	            System.out.println("no argument in cmd");
	        }
	    }
	}

9.5 自定义异常类

	class CircleException extends Exception {
	    double radius;
	    CircleException(double r) {
	        radius = r;
	    }
	    public String toString() {
	        return "半径r = " + radius + "不是一个正数";
	    }
	}
	
	class Circle {
	    private double radius;
	    public void setRadius(double r) throws CircleException {
	        if(r < 0) throw new CircleException(r);
	        else      radius = r;
	    }
	    public void show() {
	        System.out.println("圆面积：" + Math.PI * radius * radius);
	    }
	}
	
	public class Main {
	    public static void main(String[] agrs) throws CircleException{
	        Circle cir = new Circle();
	        cir.setRadius(-2);
	        cir.show();
	    }
	}

通过本章的讨论，可以看出对异常的处理不外乎两种方式：

1. 在方法内使用try - catch 语句来处理方法本身所产生的异常

2. 在方法声明的头部使用throws语句或在方法内使用throw语句将它送往上一层调用机构去处理。


## Chapter 10 Java IO和文件



## Chapter 11 多线程



## Chapter 12 泛型和容器类



## Chapter 13 图形界面设计


## Chapter 14 事件处理


## Chapter 15 绘图程序设计


## Chapter 16 小程序设计


## Chapter 17 Java数据库程序设计


## Chapter 18 Java网络编程

