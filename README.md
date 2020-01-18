# Java
<br>
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




