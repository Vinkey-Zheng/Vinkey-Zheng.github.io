# Java的基本知识点
## 基本概念
1. JDK：Java的软件开发工具包，内含一些文档和类，提供给开发人员开发。
2. JRE：Java的运行环境，基于程序员运行，有基本类，但是不能开发。
3. JVM：Java的虚拟机,JRE内的一部分，实现跨平台。
## eclipse使用要点
1. 不能直接打开一个Java文件，需要有project里面的相关文件
+ .project    .classpath(自选)
## 关键字
1. char类型实质上是int类型的一个子集。
## 经典冒泡排序
```
package sample;
public class SortTest {
    public void sort(int a[]) {
        int n = a.length;
        int t = 0;
        for(int i = n-1; i>0; i--){
            for(int j = 0; j < i; j++){
                if(a[j] > a[j+1]) {
                    t = a[j];
                    a[j] = a[j+1];
                    a[j+1] = t;
                }
            }
        }
        for(int k = 0; k < a.length; k++){
            System.out.print(a[k]+" ");
        }
    }
    public static void main(String args[]){
        int nums[] = {1,2,3,4,5,6};
        SortTest st = new SortTest();
        st.sort(nums);
    }
    
}
```
## 类与对象
基本语法如下：
1. 类的定义
+ [类修饰符] class 类名称 [extends 父类名称]
+ [implements 接口名称列表]
{  
       成员变量定义及初始化；
       
       方法定义及方法体；

}
+ 如果缺省extends子句，则该类为java.lang.Object的子类。子类可以继承父类中访问权限设定为public、protected、default的成员变量和方法，但是不能继承访问权限为private的成员变量和方法。
+ this()和super()必须放在第一条语句，this()调用的是一个构造方法对其他构造方法的调用，super()调用超类的构造方法。
    
+ 类的定义由类声明和类体组成。其中，类声明包含关键字class、类名称及类的属性。
类的修饰符有：public、abstract 、final和friendly四种，**默认方式为friendly**。
2. 成员变量的定义及修饰字
+ 对于一个成员变量，可以有访问说明符有public、private和protected三种：
+ （1）public：省略时默认为公有类型，可以由外部对象进行访问。
+ （2）private：私有类型，只允许在类内部的方法中使用，若从外部访问，必须***通过构造函数***间接进行。
+ （3）Protected：受保护类型，子类访问受到限制。 
3. 方法
其中，方法修饰符有：[public | protected | private ] [static] [final | abstract] [native] [synchronized]。
4. 在java.lang.Object中，在对对象进行垃圾收集前，Java运行时系统会自动调用对象的finalize() 方法来释放系统资源。该方法必须按如下方式声明：
protected void finalize() throws throwable{...}
+ 方法也可被重写，但要加上super.finalize();
## java面向对象的高级属性
1. 静态static:静态成员属于类的成员，不属于实例的成员，可以通过类直接调用。
```
# 静态成员变量初始化
class Example05_4  {
     static int i = 5;
     static int j = 6;
     static int k;
     static void method() {
        System.out.println(″k=″ + k);
     }
     static  {
       if(i * 5 >= j * 4) k = 10;
     }
     public static void main(String args［］) {
       Example05_4.method();
     }
 }
# 静态初始化块会在加载类时调用而且只被调用一次。
 ```

2. final类不能被继承，final类中自动生成final方法。
3. abstract抽象类，一些不含方法体的方法，它的方法体的实现交给该类的子类根据自己的情况去实现。
4. 扩展抽象类
5. 接口(interface)继承(implements)可以继承多个接口，类(class)只能继承(extends)一个爸爸。
6. 内部类(Inner Class)嵌套在类里面的类：
+ 普通成员内部类：就是没有任何关键字的内部类，可以在外部类中、外部类外访问；成员内部类可以无条件访问外部类的所有成员属性和成员方法（包括private成员和静态成员）。
+ + 不过要注意的是，当成员内部类拥有和外部类同名的成员变量或者方法时，会发生隐藏现象，即默认情况下访问的是成员内部类的成员。如果要访问外部类的同名成员，需要以下面的形式进行访问：
```
外部类.this.成员变量
外部类.this.成员方法 
```

+ 静态成员内部类：多了一个static,其他访问方法一样；不能访问外部类的非static成员；   
+ 局部内部类：局部内部类是定义在一个方法或者一个作用域里面的类，它和成员内部类的区别在于局部内部类的访问仅限于方法内或者该作用域内；
+ + 局部内部类就像是方法里面的一个局部变量一样，是不能有public、protected、private以及static修饰符的。
+ 匿名内部类(anonymous):没有类名、没有构造方法、没有修饰符,扩展一个现有的类。
```
class InnerFather {
	public void method() // 父类中的方法
	{
		System.out.println("这是内部类父类的方法");
	}
}

public class Test {
	public static void main(String[] args) {
		InnerFather nf = new InnerFather() // 创建匿名内部类
		{
			public void method() // 重写父类中的方法
			{
				System.out.println("这是匿名内部类的方法");
			}
		};
		nf.method(); // 调用匿名内部类中的方法
	}
}
```

7. 自动装箱与拆箱
+ 装箱：类(原始类型值)变为类型值(对象)
+ 拆箱：类型值(对象)变为类(原始类型值)
```
# 自动版
        int m = 500;
        Integer obj = m;  // 自动装箱
        int n = obj;  // 自动拆箱

# 通过Integer构造方法手动装箱，通过intValue()手动拆箱
public class Demo {
    public static void main(String[] args) {
        int m = 500;
        Integer obj = new Integer(m);  // 手动装箱
        int n = obj.intValue();  // 手动拆箱
        System.out.println("n = " + n);
       
        Integer obj1 = new Integer(500);
        System.out.println("obj等价于obj1的返回结果为" + obj.equals(obj1));
    }
}
```
8. 枚举
```
enum Day {
	MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY
}
public class EnumTest {
	public static void main(String[] args) {
		// 创建枚举数组
		Day[] days = new Day[] { Day.MONDAY, Day.TUESDAY, Day.WEDNESDAY,
				Day.THURSDAY, Day.FRIDAY, Day.SATURDAY, Day.SUNDAY };
		// 打印枚举常量的序号以及枚举值
		for (int i = 0; i < days.length; i++) {
			System.out.println("day[" + days[i].ordinal() + "]:"
					+ days[i].name());
		}
		// 通过compareTo方法比较,实际上其内部是通过ordinal()值比较的
		System.out.println("day[1] VS day[2]:" + days[1].compareTo(days[2]));
	}
} 
```
9. 同 class 和 interface 一样，注解也属于一种类型。它的形式跟接口很类似，不过前面多了一个 @ 符号。
```
# java提供的5个基本注解方法：@Override、@Deprecated、@SuppressWarnings、@SafeVarargs、@FunctionalInterface
```
```
# 指定某个接口是函数式接口
# java8中规定如果接口中只有一个抽象方法，那么该接口就是函数式接口。@FunctionalInterface就是用来指定某个接口必须是函数式接口，而且它只能用来修饰接口，不能修饰其它元素。
@FunctionalInterface
public interface FITest {
	    public void test1(); 
}    
```
10. 它可以使用一种简洁的方式来创建只有一个抽象方法的接口（函数式接口）的实例
```
lambda 表达式的语法格式如下：
    (Parameters) -> Expression  或
    (Parameters) ->{ Statements; }
前面介绍的匿名内部类的例子中，采用new对象创建匿名内部类并完成对方法的访问。
InnerFather nf=new InnerFather()  //创建匿名内部类
{
public void method()                  
{
	System.out.println(val); //访问局部变量
	}
};
以上程序采用Lambda表达式的简化写法如下：
InnerFather nf = ( ) ->System.out.println(val);
```
# Java实用类及接口
## 将字符串转换为数值类型
在 Integer 和 Float 类中分别提供了以下两种方法：

(1) Integer 类（String 转 int 型）
```
int parseInt(String s);
s 为要转换的字符串。
```

(2) Float 类（String 转 float 型）
```
float parseFloat(String s)
```
注意：使用以上两种方法时，字符串中的数据必须由数字组成，否则转换时会出现程序错误。

(3) 将整数转换为字符串
Integer 类有一个静态的 toString() 方法，可以将整数转换为字符串.
## String类
```
两种创建方式
String str1 = "hello";
String str2 = new String("hello");


//调用6个不同的构造函数来创建String对象
//空字符
String s1 = new String();
//指定字符串和字符组
String s2 = new String( s );
//下标为6，往后连续3个字符
String s3 = new String( charArray, 6, 3 );
```
valueOf()方法的应用
```
class Example6_2{
	//覆盖Object类中的toString（）方法
	public String toString(){
		return "example";
	}
}
class ValueOfTest {
	public static void main(String[] args)	{
		char c=0x41;
		int i=0x41;
		boolean b=i==c;
		Example6_2 obj=new Example6_2();
		char[] chars={'a','1','b','2'};
		System.out.print(String.valueOf(b)+" ");
		System.out.print(String.valueOf(c)+" ");
		System.out.print(String.valueOf(i)+" ");
		System.out.print(String.valueOf(obj)+" ");
		System.out.println(String.valueOf(chars)+" ");
	}
}
```
结果如下：
```
true A 65 example a1b2
```
getChars() 方法将字符从字符串复制到目标字符数组。

public void getChars(int srcBegin, int srcEnd, char[] dst,  int dstBegin)

参数

srcBegin -- 字符串中要复制的第一个字符的索引。

srcEnd -- 字符串中要复制的最后一个字符之后的索引。

dst -- 目标数组。

dstBegin -- 目标数组中的起始偏移量。
```
public class Example6_7{
    public static void main(String args[]) {
        String s = " Hello, Java,  Stri\tng ";
        System.out.println("s原始值: " + s);
        System.out.println("判断字符串是否为空:" + s.isBlank());
        System.out.println("去掉首尾空格:" + s.strip());
        System.out.println("去掉尾空格:" + s.stripTrailing());
        System.out.println("去掉首空格:" + s.stripLeading());
        System.out.println("字符串重复:" + s.repeat(3));
        System.out.println("行数统计:" + s.lines().count());
 
    }
}
```
## 注意小点
1. float变量初始化要加f, 不然默认是double