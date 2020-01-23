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

![IO类关系图](https://www.png8.com/imgs/2020/01/52794b5f9772ce39.jpg)

10.1 Java语言的输入输出类库

10.2 使用Input和OutputStream流类

1. 文件输入输出

		import java.io.*;
	
		class Main {
		    public static void main(String[] agrs) {
		        FileInputStream fin;
		        FileOutputStream fout;
		        char ch;
		        int data;
		        try {
		            fin = new FileInputStream(FileDescriptor.in);
		            fout = new FileOutputStream("C:\\Users\\Jianan Yuan\\Desktop\\test.txt");
		            System.out.println("输入，按 # 结束");
		            while((ch = (char)fin.read()) != '#') {
		                fout.write(ch);
		            }
		            fin.close();
		            fout.close();
		            System.out.println();
		            fin = new FileInputStream("C:\\Users\\Jianan Yuan\\Desktop\\test.txt");
		            fout = new FileOutputStream(FileDescriptor.out);
		            while(fin.available() > 0) {
		                data = fin.read();
		                fout.write(data);
		            }
		            fin.close();
		            fout.close();
		        } catch(FileNotFoundException e) {
		            System.out.println( "文件没找到");
		        } catch(IOException e) {
		            System.out.println("文件异常");
		        }
		    }
		}

------

	import java.io.FileInputStream;
	import java.io.FileOutputStream;
	import java.io.IOException;
	
	class Main  {
	    public static void main(String[] agrs) throws IOException {
	        FileInputStream fin = new FileInputStream("C:\\Users\\Jianan Yuan\\Music\\Delacey - Dream It Possible.mp3");
	        FileOutputStream fout = new FileOutputStream("C:\\Users\\Jianan Yuan\\Desktop\\copy.wav");
	        System.out.println("size = " + fin.available());
	        byte[] b = new byte[fin.available()];
	        fin.read(b);
	        fout.write(b);
	        fin.close();
	        fout.close();
	
	    }
	}

2. 顺序输入流

3. 管道输入输出流

4. 过滤输入输出流

注意DataOutputStream和DataInputStream的灵活使用

5. 标准输入输出

10.3 使用Reader和Writer

1. FileReader

2. FileWriter

3. BufferedReader

		import java.io.BufferedReader;
		import java.io.FileReader;
		import java.io.IOException;
		
		public class Main {
		    public static void main(String[] agrs) {
		        String thisLine;
		        int cnt = 0;
		        try {
		            BufferedReader buf = new BufferedReader(new FileReader("C:\\Users\\Jianan Yuan\\Desktop\\test.txt"));
		            while((thisLine = buf.readLine()) != null) {
		                cnt++;
		                System.out.println(thisLine);
		            }
		            System.out.println("一共读取了" + cnt + "行");
		            buf.close();
		        } catch(IOException e) {
		            System.out.println("读写异常");
		        }
		    }
		}


4. BufferedWriter

10.4 文件的处理与随机访问



## Chapter 11 多线程



## Chapter 12 泛型和容器类



## Chapter 13 图形界面设计

13.1 图形用户界面概述

13.2 图形用户界面工具包 —— Swing
 
	// 基本框架演示

	// MyFrame.java

	import javax.swing.*;
	import java.awt.*;
	import java.awt.event.ActionEvent;
	import java.awt.event.ActionListener;
	import java.text.SimpleDateFormat;
	import java.util.Date;
	
	public class MyFrame extends JFrame {
	    JLabel timeLabel = new JLabel("00:00:00");
	    JButton button = new JButton("显示时间");
	
	    public MyFrame(String s) {
	        super(s);
	        Container contentPane = getContentPane();
	        contentPane.setLayout(new FlowLayout());
	        contentPane.add(button);
	        showTime();
	        contentPane.add(timeLabel);
	        button.addActionListener(new ActionListener() {
	            @Override
	            public void actionPerformed(ActionEvent e) {
	                showTime();
	            }
	        });
	    }
	
	    public void showTime() {
	        SimpleDateFormat sdf = new SimpleDateFormat("HH:mm:ss");
	        String timestr = sdf.format(new Date());
	        timeLabel.setText(timestr);
	    }
	}


	// Main
	import javax.swing.*;
	
	public class Main {
	    private static void CreateGUI() {
	        MyFrame frame = new MyFrame("Swing Demo");
	        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
	        frame.setSize(400,300);
	        frame.setVisible(true);
	    }
	
	    public static void main(String[] args) {
	        CreateGUI();
	    }
	}

示例

	

	import javax.swing.*;
	import java.awt.*;
	import java.awt.event.ActionEvent;
	import java.awt.event.ActionListener;
	
	public class MyFrame extends JFrame {
	    JComboBox<String> colorList = new JComboBox<>();
	    JLabel label = new JLabel(" 文本示例 This is a Sample");
	
	    public MyFrame(String name) {
	        super(name);
	        Container cta = getContentPane();
	        cta.setLayout(new FlowLayout());
	        cta.add(colorList);
	        cta.add(label);
	        colorList.addItem("red");
	        colorList.addItem("blue");
	        colorList.addItem("green");
	        update();
	        colorList.addAct		ionListener(new ActionListener() {
	            @Override
	            public void actionPerformed(ActionEvent e) {
	                update();
	            }
	        });
	    }
	
	    public void update() {
	        String color = (String)colorList.getSelectedItem();
	        Color c = null;
	        if(color.equals("red")) {
	            c = Color.RED;
	        } else if(color.equals("green")) {
	            c = Color.GREEN;
	        } else {
	            c = Color.BLUE;
	        }
	        label.setForeground(c);
	    }
	}

示例

	import javax.swing.*;
	import java.awt.*;
	
	public class MyFrame extends JFrame {
	    private JLabel jl1 = new JLabel("hello java!");
	    private JLabel jl2 = new JLabel("文本示例");
	
	    public MyFrame(String name) {
	        super(name);
	        Container cta = getContentPane();
	        cta.setLayout(new SampleLayout());
	        cta.add(jl1);
	        cta.add(jl2);
	    }
	
	    private class SampleLayout implements LayoutManager {
	
	        @Override
	        public void addLayoutComponent(String name, Component comp) {
	
	        }
	
	        @Override
	        public void removeLayoutComponent(Component comp) {
	
	        }
	
	        @Override
	        public Dimension preferredLayoutSize(Container parent) {
	            return null;
	        }
	
	        @Override
	        public Dimension minimumLayoutSize(Container parent) {
	            return null;
	        }
	
	        @Override
	        public void layoutContainer(Container parent) {
	            int w = parent.getWidth();
	            int h = parent.getHeight();
	            System.out.println("father: " + w + "," + h);
	            if(jl1.isVisible()) {
	                Dimension size = jl1.getPreferredSize();
	                int x = (w - size.width) / 2;
	                int y = (h - size.height) / 2;
	                jl1.setBounds(x,y,size.width,size.height);
	            }
	            if(jl2.isVisible()) {
	                Dimension size = jl2.getPreferredSize();
	                int x = (w - size.width);
	                int y = 0;
	                jl2.setBounds(x,y,size.width,size.height);
	            }
	        }
	    }
	}

示例

	import javax.swing.*;
	import java.applet.Applet;
	import java.applet.AudioClip;
	import java.awt.*;
	import java.awt.event.ActionEvent;
	import java.awt.event.ActionListener;
	import java.awt.event.MouseEvent;
	import java.awt.event.MouseListener;
	import java.io.File;
	import java.net.MalformedURLException;
	import java.net.URL;
	
	public class MyFrame extends JFrame {
	    AudioClip auu ;
	    public MyFrame(String name) {
	        super(name);
	        JPanel root = new JPanel();
	        setContentPane(root);
	        root.setLayout(new BorderLayout());
	        JMenuBar menubar = new JMenuBar();
	        setJMenuBar(menubar);
	        JMenu fileMenu = new JMenu("文件");
	        menubar.add(fileMenu);
	        JMenuItem fileOpenCmd  = new JMenuItem("打开");
	        JMenuItem fileSaveCmd  = new JMenuItem("保存");
	        JMenuItem fileSaveAsCmd  = new JMenuItem("另存为...");
	        fileMenu.add(fileOpenCmd);
	        fileMenu.add(fileSaveCmd);
	        fileMenu.add(fileSaveAsCmd);
	        fileMenu.addSeparator();
	        JMenuItem exit = new JMenuItem("退出");
	        exit.addActionListener(new ActionListener() {
	            @Override
	            public void actionPerformed(ActionEvent e) {
	                System.exit(0); 
	            }
	        });
	        fileMenu.add(exit);
	
	        JMenu help = new JMenu("帮助");
	        JMenuItem about = new JMenuItem("关于");
	        JMenuItem hhelp = new JMenuItem("打开帮助");
	        help.add(about);
	        help.addSeparator();
	        help.add(hhelp);
	        menubar.add(help);
	
	    }
	}

示例

	import sun.plugin.javascript.navig.Image;

	import javax.swing.*;
	import java.applet.Applet;
	import java.applet.AudioClip;
	import java.awt.*;
	import java.awt.event.ActionEvent;
	import java.awt.event.ActionListener;
	import java.awt.event.MouseEvent;
	import java.awt.event.MouseListener;
	import java.io.File;
	import java.net.MalformedURLException;
	import java.net.URL;
	
	public class MyFrame extends JFrame {
	    public MyFrame(String name) {
	        super(name);
	        JPanel jp = new JPanel();
	        setContentPane(jp);
	        jp.setLayout(new BorderLayout());
	        JToolBar jbt = new JToolBar();
	        jbt.setFloatable(false);
	        jp.add(jbt,BorderLayout.PAGE_START);
	        jbt.add(toolButton("打开.png","file_open","open"));
	        jbt.add(toolButton("保存.png","file_save","save"));
	        jbt.add(toolButton("另存为.png","file_saveas","save as"));
	        jbt.addSeparator();
	        jbt.add(toolButton("帮助.png","file_help","help"));
	        JLabel jl = new JLabel("123");
	        jl.setIcon(new ImageIcon(("D:\\IDEA文件\\绩点计算器\\src\\icon\\香港地铁.png")));
	        jp.add(jl,BorderLayout.CENTER);
	
	    }
	
	    protected JButton toolButton(String imageName,String action,String prompt) {
	        URL imageURL = getClass().getResource("/icon/" + imageName);
	        JButton jb = new JButton();
	        jb.setActionCommand(action);
	        jb.setToolTipText(prompt);
	        jb.setIcon(new ImageIcon(imageURL));
	        jb.setFocusPainted(false);
	        jb.addActionListener(actionListener);
	        return jb;
	    }
	
	    private ActionListener actionListener = new ActionListener() {
	        @Override
	        public void actionPerformed(ActionEvent e) {
	            String action  = e.getActionCommand();
	            System.out.println(action);
	            if(action.equals("file_open")) {
	                JOptionPane.showMessageDialog(MyFrame.this,action);
	            }
	        }
	    };
	}

示例

	import sun.plugin.javascript.navig.Image;
	
	import javax.swing.*;
	import java.applet.Applet;
	import java.applet.AudioClip;
	import java.awt.*;
	import java.awt.event.*;
	import java.io.File;
	import java.net.MalformedURLException;
	import java.net.URL;
	
	public class MyFrame extends JFrame {
	    public MyFrame(String name) {
	        super(name);
	        JPanel jp = new JPanel();
	        setContentPane(jp);
	        jp.setLayout(new BorderLayout());
	        JPopupMenu jpo = new JPopupMenu();
	        jpo.add(createMenuItem("打开","file_open","打开.png"));
	        jpo.add(createMenuItem("保存","file_save","保存.png"));
	        jpo.add(createMenuItem("另存为","file_saveas","另存为.png"));
	        jp.addMouseListener(new MouseAdapter() {
	            @Override
	            public void mouseClicked(MouseEvent e) {
	                if(e.getButton() == MouseEvent.BUTTON3) {
	                    jpo.show(e.getComponent(),e.getX(),e.getY());
	                }
	            }
	        });
	    }
	
	    protected JMenuItem createMenuItem(String name,String action,String path) {
	        JMenuItem it = new JMenuItem(name);
	        it.setActionCommand(action);
	        it.addActionListener(actionListener);
	        it.setIcon(new ImageIcon(getClass().getResource("/icon/" + path)));
	        return it;
	    }
	
	    private ActionListener actionListener = new ActionListener() {
	        @Override
	        public void actionPerformed(ActionEvent e) {
	            String action = e.getActionCommand();
	            System.out.println(action);
	            if(action.equals("file_open")) {
	                JOptionPane.showMessageDialog(MyFrame.this,action);
	            }
	        }
	    };
	}

示例

	import sun.plugin.javascript.navig.Image;

	import javax.swing.*;
	import java.applet.Applet;
	import java.applet.AudioClip;
	import java.awt.*;
	import java.awt.event.*;
	import java.io.File;
	import java.net.MalformedURLException;
	import java.net.URL;
	
	public class MyFrame extends JFrame {
	    public MyFrame(String name) {
	        super(name);
	        JPanel jp = new JPanel();
	        setContentPane(jp);
	        jp.setLayout(new FlowLayout());
	        JButton jb = new JButton("test");
	        jp.add(jb);
	        jb.addActionListener(new ActionListener() {
	            @Override
	            public void actionPerformed(ActionEvent e) {
	                String str = getUserInput();
	                System.out.println("用户输入了: " + str);
	            }
	        });
	    }
	
	    protected String getUserInput() {
	        JDialog jd = new JDialog(this,"test",true);
	        JPanel jp = new JPanel();
	        jp.setLayout(new FlowLayout());
	        jd.setContentPane(jp);
	        JTextField jl = new JTextField(16);
	        JButton jb = new JButton("confirm");
	        jd.add(jl);
	        jd.add(jb);
	        jb.addActionListener(new ActionListener() {
	            @Override
	            public void actionPerformed(ActionEvent e) {
	                jd.setVisible(false);
	            }
	        });
	        jd.setSize(300,100);
	        jd.setVisible(true);
	        String rec = jl.getText();
	        return rec;
	    }
	}


示例

	import sun.plugin.javascript.navig.Image;

	import javax.swing.*;
	import javax.swing.border.Border;
	import java.applet.Applet;
	import java.applet.AudioClip;
	import java.awt.*;
	import java.awt.event.*;
	import java.io.File;
	import java.net.MalformedURLException;
	import java.net.URL;
	
	public class MyFrame extends JFrame {
	    public MyFrame(String name) {
	        super(name);
	        JPanel jp = new JPanel();
	        jp.setLayout(new BorderLayout());
	        setContentPane(jp);
	        DefaultListModel<String> jl = new DefaultListModel<>();
	        jl.addElement("123");
	        // ... 
	
	        JList<String> jll= new JList<>();
	        jll.setModel(jl);
	        jll.setSelectionMode(ListSelectionModel.SINGLE_SELECTION);
	
	        JScrollPane js = new JScrollPane(jll);
	
	        jp.add(js,BorderLayout.CENTER);
	
	    }
	}

示例

	import com.sun.xml.internal.ws.api.streaming.XMLStreamReaderFactory;

	import javax.swing.*;
	import javax.swing.event.TableModelListener;
	import javax.swing.table.DefaultTableCellRenderer;
	import javax.swing.table.DefaultTableModel;
	import javax.swing.table.TableModel;
	import java.awt.*;
	import java.util.Vector;
	
	public class MyFrame extends JFrame {
	
	    DefaultTableModel tm = new DefaultTableModel();
	
	    public MyFrame (String name) {
	        super(name);
	        JPanel jp = new JPanel();
	        jp.setLayout(new BorderLayout());
	        setContentPane(jp);
	
	        Student stu[] = {new Student("19635","JiananYuan","male","大一","中国大陆"),
	                new Student("10001","Cralim.K","female","研究生","美国加州"),
	                new Student("15630","Maria Zheng","female","大二","中国香港")};
	
	        tm.addColumn("唯一编号");
	        tm.addColumn("名字");
	        tm.addColumn("性别");
	        tm.addColumn("年级");
	        tm.addColumn("地区");
	
	        for(int i=0;i<3;i++) {
	            Vector<Object> v = new Vector<>();
	            v.add(stu[i].num);
	            v.add(stu[i].name);
	            v.add(stu[i].sex);
	            v.add(stu[i].grade);
	            v.add(stu[i].area);
	            tm.addRow(v);
	        }
	
	        JTable jt = new JTable();
	        jt.setModel(tm);
	        jt.setFont(new Font("楷体",Font.BOLD,25));
	        jt.getTableHeader().setFont(new Font("微软雅黑",0,25));
	        jt.setFillsViewportHeight(true);
	        jt.setRowHeight(30);
	        // jt.setRowSelectionAllowed(true);
	        JScrollPane js = new JScrollPane(jt);
	        jp.add(js,BorderLayout.CENTER);
	    }
	}
	
	class Student {
	    String num;
	    String name;
	    String sex;
	    String grade;
	    String area;
	    Student(String a,String b,String c,String d,String e) {
	        num = a;
	        name = b;
	        sex = c;
	        grade = d;
	        area = e;
	    }
	}


13.3 创建组件

13.4 布局管理器


## Chapter 14 事件处理

14.1 Java语言的事件处理机制 —— 委托事件模型

14.2 Java语言的事件类

14.3 适配器类

14.4 命令按钮及相应的事件处理

14.5 复选框、单选按钮相应的事件处理

14.6 文本组件及相应的事件处理

14.7 窗口组件及窗口事件处理

14.8 对话框设计及相应的事件处理

14.9 按键事件类及相应的事件处理

14.10 鼠标事件类及相应的事件处理

14.11 列表框及相应的事件处理

14.12 组合框及相应的事件处理

14.13 菜单设计

14.14 工具栏设计

14.15 滑动条设计及相应的事件处理

14.16 文件选择对话框

14.17 颜色选择对话框

14.18 定时器


## Chapter 15 绘图程序设计



## Chapter 16 小程序设计



## Chapter 17 Java数据库程序设计



## Chapter 18 Java网络编程

18.1 网络基础

针对不同层次的网络通信，Java语言提供的网络功能有四大类：URL（面向应用层）,InetAddress（面向IP层），Socket，Datagram（面向传输层）

18.2 URL编程

	import java.io.BufferedReader;
	import java.io.IOException;
	import java.io.InputStreamReader;
	import java.net.MalformedURLException;
	import java.net.URL;
	
	public class Main {
	    public static void main(String[] args) {
	        try {
	            URL url = new URL("http://www.edu.cn/index.html");
	            BufferedReader br = new BufferedReader(new InputStreamReader(url.openStream()));
	            String s;
	            while((s = br.readLine()) != null) {
	                System.out.println(s);
	            }
	        } catch(MalformedURLException e) {
	            System.out.println(e);
	        } catch(IOException e) {
	            System.out.println(e);
	        }
	    }
	}

读取网络上的文件内容一般分3个步骤：

创建URL对象，利用URL对象的openstream方法获得对应的InputStream对象，通过InputStream对象来读取文件内容

18.3 用Java语言实现底层网络通信

18.3.1 InetAddress程序设计

public static InetAddress getByName(String name) // name --> InetAddress

public static InetAddress getByAddress(String name) // ip --> InetAddress

public static InetAddress getLocalHost()

public byte[] getAddress()

public String getHostAddress()

public String getHostName()

public String toString()


18.3.2 基于连接的Socket通信程序设计

Socket类的构造方法：

public Socket(String host,int port)

public Socket(InetAddress address,int port)

public Socket(String host,int port,boolean stream)

public Socket(InetAddress host,int port,boolean stream)

常用方法：

public InetAddress getInetAddress()

public InetAddress getLocalAddress()

public InputStream getInputStream()

public OutputStream getOutputStream()

public int getPort()

public void setRecieveBufferSize()

public int getRecieveBufferSize()

SeverSocket类的构造方法：

public SeverSocket(int port)

public SeverSocket(int port,int backlog)

Socket通信模式：

1. 客户建立到服务器的套接字对象

2. 建立接受客户套接字的服务器套接字



18.3.3 无连接的数据报通信程序设计

