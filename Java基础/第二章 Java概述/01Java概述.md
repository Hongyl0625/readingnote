# Java概述

## Java历史

- 1990 sun公司 启动 绿色计划
- 1992 创建 oak(橡树)语言 -> java
- 1994 gosling 参加 硅谷大会，演示java功能，震惊世界。
- **1995 sun正式发布Java的第一个版本。**
- 2009 甲骨文收购sun公司。

## Java特点

1. Java语言是面向对象的（oop）

2. Java语言是健壮的。Java的强类型机制、异常处理、垃圾的自动收集等是Java程序健壮性的重要保证

3. Java语言是跨平台性的，即：一个编译好的.class文件可以在多个系统【linux/windows】下运行，这种特性被称为跨平台性

4. Java语言是解释型的【了解】

   解释型语言：javascript、PHP、Java 编译型语言：c、c++

   区别是：解释型语言，编译后的代码，不能直接被机器执行，需要解释器来执行；编译语言，编译后的代码，可以直接被机器执行。

## Java运行机制及运行过程

- Java核心机制-Java虚拟机【JVM java virtual machine】

- 基础介绍

  1. JVM是一个虚拟的计算机，具有指令集使用不同的存储区域。负责执行指令，管理数据、内存、寄存器，包含在JDK中。
  2. 对于不同的平台，有不同的虚拟机【windows/linux/macos】。
  3. Java虚拟机机制屏蔽了底层运行平台的差别，实现了【一次编译，到处运行】
  4. 示意图

  ![image-20211026111640089](/Users/hongyuliang/Library/Application Support/typora-user-images/image-20211026111640089.png)

	### 什么是JDK、JRE

- JDK基本介绍

  1. JDK全称（Java Development Kit	Java开发工具包）

     JDK = JRE + java的开发工具【java，javac，javadoc，javap等】

  2. JDK是提供给Java开发人员使用的，其中包含了java的开发工具，也包括了JRE。所以安装了JDK，就不用单独安装JRE了。

- JRE基本介绍

  1. JRE全称（Java Runtime Enviroment	Java运行环境）

     JRE = JVM + java核心类库

  2. 包括Java虚拟机（JVM    Java Virtual Machine）和Java程序所需的核心类库等，如果想要运行一个开发好的Java程序（.class文件），计算机中只需要安装JRE即可。

- JDK、JRE和JVM的包含关系

  1. jdk = jre+java开发工具集
  2. jre = jvm + java SE核心类库

  如果只想运行开发好的.class文件，只需要安装jre即可。

## Java开发环境搭建

## DOS常用指令

## 实例1

### 需求说明

要求写一个Hello.java程序，可以输出"hello, world!"

### 开发步骤

1. 将java代码编写到名为Hello.java的文件中
2. 通过【javac】命令对该文件进行编译，生成.class文件
3. 通过【java】命令对生成的class文件进行运行

### 运行原理示意图

![image-20211026111640089](/Users/hongyuliang/Library/Application Support/typora-user-images/image-20211026111640089.png)

java.exe执行的本质是将.java文件（源文件）编译后生成.class文件（字节码文件）。

java.exe执行的本质是将.class文件（字节码文件）装载到JVM(虚拟机)中进行执行。



## Java开发注意事项和细节说明

1. Java源文件以.java为扩展名。源文件的基本组成部分是类（class），如本类中的Hello类。

2. Java应用程序的执行入口是main()方法。它有固定的书写格式：

   public static void main(String[] args) {...}

3. Java语言严格区分大小写。
4. Java方法由一条条语句构成，每个语句以“;”结束。
5. 大括号都是成对出现的，缺一不可。
6. 一个源文件中**最多只能有一个public类**。非public类个数不限。【演示1】
7. 如果源文件包含一个public类，则文件名必须按照这个public类名命名。
8. 可以将main方法写在非public类中，然后指定运行非public类，这样入口方法就是非public类的main方法。【演示2】

### 演示1

```java
public class Hello {

	public static void main(String[] args) {
		System.out.println("hello,world!");
	}
}

// 一个源文件中最多只能有一个public类。非public类个数不限。
class Dog {}

class Tiger {}
```

### 演示2

```java
public class Hello {

	public static void main(String[] args) {
		System.out.println("hello,world!");
	}
}

// 一个源文件中最多只能有一个public类。非public类个数不限。
class Dog {

	public static void main(String[] args) {
		System.out.println("hello,小狗狗～");
	}
}

class Tiger {

	public static void main(String[] args) {
		System.out.println("hello,小老虎～");
	}
}
```

## Java转义字符

- Java常用的转义字符

  1. `\t` 制表符，实现对齐的功能
  2. `\n` 换行符
  3. `\\` 一个\
  4. `\"`一个"
  5. `\'`一个'
  6. `\r`回车符

  



