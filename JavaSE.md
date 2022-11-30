##### Java Standard Problems

###### JVM JDK JRE 是什么？

- Java 虚拟机（JVM）是运行 Java 字节码的虚拟机。
- JVM 有针对不同系统的特定实现（Windows，Linux，macOS），目的是使用相同的字节码(.class 文件)，它们都会给出相同的结果。

“一次编译 多次运行"

- JDK 是 Java Development Kit，它是功能齐全的 Java SDK。它拥有 JRE 所拥有的一切，还有编译器（javac）和工具（如 javadoc 和 jdb）。它能够创建和编译程序。
- JRE 是 Java 运行时环境。它是运行已编译 Java 程序所需的所有内容的集合，包括 Java 虚拟机（JVM），Java 类库，java 命令和其他的一些基础构件。但是，它不能用于创建新程序。
- JVM

执行过程？

- .java -> .class 文件 借助于 jdk中的编译器编译成字节码
- .class 文件 JVM能看懂 用JVM去执行

###### Java文件里可以有多个class吗？

- 可以有多个class 在用javac工具编译时 编译出多个.class字节码文件

- 如果定义public class的类，只能定义一个，并且要求此类名必须和java源文件名保持一致。

###### 标识符 关键字

- 标识符（identifier）是指用来标识某个实体的一个符号，在不同的应用环境下有不同的含义。-》起名字

- Java关键字是编程语言里事先定义的，有特殊意义的单词，
- 标识符只能由数字、字母、下划线“_”、美元符号“$”组成，不能含有其它符号。

变量种类

- 局部变量 ： 写在方法体内的变量

- 成员变量 ：定义在java class类中的变量

###### 运算符

& 与 && 区别？- 短路效应 Leetcode 1905

helper() -> boolean

boolean right = helper(arg1) & helper(arg2)

boolean right = helper(arg1) && helper(arg2)

###### 方法重载

- 在同一个类中，方法名相同，参数列表不同。与返回值类型无关。
- 参数列表不同：参数个数不同，参数类型不同

###### 基本数据类型 引用数据类型

方法参数是基本数据类型，传递的是值。12方法参数是引用数据类型

方法参数是引用数据类型方法参数是引用类型时，传递的是内存地址值。

基本类型作为参数传递时，其实就是将基本类型变量x空间中的值复制了一份传递给调用的方法show()，当在show()方法中x接受到了复制的值，再在show()方法中对x变量进行操作，这时只会影响到show中的x。当show方法执行完成，弹栈后，程序又回到main方法执行，main方法中的x值还是原来的值。

当引用变量作为参数传递时，这时其实是将引用变量空间中的内存地址(引用)复制了一份传递给了show方法的d引用变量。这时会有两个引用同时指向堆中的同一个对象。当执行show方法中的d.x=6时，会根据d所持有的引用找到堆中的对象，并将其x属性的值改为6.show方法弹栈。

#### 面向对象

##### 概念

面向过程与面向对象都是我们编程中，编写程序的一种思维方式

* a: 面向过程的程序设计方式，是遇到一件事时，思考“我该怎么做”，然后一步步实现的过程。
* b: 面向对象的程序设计方式，是遇到一件事时，思考“我该让谁来做”，然后那个“谁”就是对象，他要怎么做这件事是他自己的事，反正最后一群对象合力能把事就好就行了。

##### 成员变量 局部变量

* 区别一：定义的位置不同
  * 定义在类中的变量是成员变量
  * 定义在方法中或者{}语句里面的变量是局部变量
* 区别二：在内存中的位置不同
  * 成员变量存储在堆内存的对象中
  * 局部变量存储在栈内存的方法中
* 区别三：声明周期不同
  * 成员变量随着对象的出现而出现在堆中，随着对象的消失而从堆中消失
  * 局部变量随着方法的运行而出现在栈中，随着方法的弹栈而消失
* 区别四：初始化不同
  * 成员变量因为在堆内存中，所有默认的初始化值
  * 局部变量没有默认的初始化值，必须手动的给其赋值才可以使用。

##### 构造方法

* 名字与类名相同。
* 没有返回值，但不能用 void 声明构造函数。
* 生成类的对象时自动执行，无需调用

#### 面向对象三大特性

##### 封装

封装是指把一个对象的状态信息（也就是属性）隐藏在对象内部，不允许外部对象直接访问对象的内部信息。但是可以提供一些可以被外界访问的方法来操作属性 主要利用private关键字

```java
public class Student {
    private int id;//id属性私有化
    private String name;//name属性私有化

    //获取id的方法
    public int getId() {
        return id;
    }

    //设置id的方法
    public void setId(int id) {
        this.id = id;
    }

    //获取name的方法
    public String getName() {
        return name;
    }

    //设置name的方法
    public void setName(String name) {
        this.name = name;
    }
}
```

##### 继承

继承的概念

继承描述的是事物之间的所属关系，通过继承可以使多种事物之间形成一种关系体系

在Java中，类的继承是指在一个现有类的基础上去构建一个新的类，构建出来的新类被称作子类，现有类被称作父类

继承关系的子类特点：子类会自动拥有父类所有非private修饰的属性和方法

```Java
*Employee.java:
		 /*
		 * 定义员工类Employee
		 */
		class Employee {
			String name; // 定义name属性

			public void work() {// 定义员工的工作方法
				System.out.println("尽心尽力地工作");
			}
		}
    *Developer.java:
	    /*
		 * 定义研发部员工类Developer 继承 员工类Employee
		 * 继承了父类中所有非private修饰的成员变量
		 */
		class Developer extends Employee {
			// 定义一个打印name的方法
			public void printName() {
				System.out.println("name=" + name);
			}
		}
    *测试员工类与研发部员工类:
        /*
	     * 定义测试类
         */
		public class Example01 {
			public static void main(String[] args) {
				Developer d = new Developer(); // 创建一个研发部员工类对象
				d.name = "小明"; // 为该员工类的name属性进行赋值
				d.printName(); // 调用该员工的printName()方法
				d.work(); // 调用Developer类继承来的work()方法
			}
		}
    *通过子类对象既可以调用自身的非private修饰的成员,也可以调用父类的非private修饰的成员
```

*A:继承的注意事项
	 *a:在Java中，类只支持单继承，不允许多继承，也就是说一个类只能有一个直接父类，例如下面这种情况是不合法的。
	     class A{}
	     class B{}
	     class C extends A,B{}  // C类不可以同时继承A类和B类
      *b:多个类可以继承一个父类，例如下面这种情况是允许的(就像你爹可以多个儿子,但是这些儿子都只有一个爹)
	     class A{}
	     class B extends A{}
	     class C extends A{}   // 类B和类C都可以继承类A

    *c:在Java中，多层继承是可以的，
        即一个类的父类可以再去继承另外的父类，
        例如C类继承自B类，而B类又可以去继承A类，这时，C类也可称作A类的子类。下面这种情况是允许的。
	     class A{}
	     class B extends A{}   // 类B继承类A，类B是类A的子类
	     class C extends B{}   // 类C继承类B，类C是类B的子类，同时也是类A的子类

    *d:在Java中，子类和父类是一种相对概念，
        也就是说一个类是某个类父类的同时，也可以是另一个类的子类。
        例如上面的这种情况中，B类是A类的子类，同时又是C类的父类。

```java
 A:继承后子类父类成员变量的特点
   a:子类的对象调用成员变量的时候,子类自己有,使用子类,子类自己没有调用的父类
	   class Fu{
			//Fu中的成员变量。
			int num = 5;
		}

		class Zi extends Fu{
			//Zi中的成员变量
			int num2 = 6;
			//Zi中的成员方法
			public void show()
			{
				//访问父类中的num
				System.out.println("Fu num="+num);
				//访问子类中的num2
				System.out.println("Zi num2="+num2);
			}
		}

		class Demo{
			public static void main(String[] args) 
			{
				Zi z = new Zi(); //创建子类对象
				z.show(); //调用子类中的show方法
			}
		}
 b:当子父类中出现了同名成员变量
	class Fu{
		//Fu中的成员变量。
		int num = 5;
	}

	class Zi extends Fu{
		//Zi中的成员变量
		int num = 6;
		void show(){   
			//子类的局部变量
			int num=7

			//直接访问,遵循就近查找原则
            System.out.println(num);//7

			//子父类中出现了同名的成员变量时
			//在子类中需要访问父类中非私有成员变量时，需要使用super关键字
			//访问父类中的num
			System.out.println("Fu num="+super.num);//5


			//访问子类中的num2
			System.out.println("Zi num2="+this.num);//6
		}
	}

	class Demo5 {
		public static void main(String[] args) 
		{
			Zi z = new Zi(); //创建子类对象
			z.show(); //调用子类中的show方法
		}
	}
```

```java
A:继承后子类父类成员方法的特性
  a:子类的对象调用方法的时候,子类自己有,使用子类,子类自己没有调用的父类
    class Fu{
		public void show(){
			System.out.println("Fu类中的show方法执行");
		}
	}
	class Zi extends Fu{
		public void show2(){
			System.out.println("Zi类中的show2方法执行");
		}
	}
	public  class Test{
		public static void main(String[] args) {
			Zi z = new Zi();
			z.show(); //子类中没有show方法，但是可以找到父类方法去执行
			z.show2();
		}
	}  
 
 b:为什么要有重写?
     class Fu{
     	public void method(){
     		//上千行代码
            //Fu类中的方法最先存在,那么如果项目需求变了,该方法
            //功能不能够满足我们的需求,此时我们也不会去改这个方法
            //因为项目中可能有大量的功能已经使用到该方法,如果随意修改可能使调用该方法的功能出现问题
            //所以使用重写方式基于原有功能提供更强的功能
     	}   
     }
     class Zi extends Fu{
  
     }
 c:子类中出现与父类一模一样的方法时，会出现覆盖操作，也称为override重写、复写或者覆盖
   class Fu{
		public void show(){
			System.out.println("Fu show");
		}
   }
   
   class Zi extends Fu{
		//子类复写了父类的show方法
		public void show(){
			System.out.println("Zi show");
		}
	}
   public  class Test{
		public static void main(String[] args) {
			Zi z = new Zi();
			z.show(); //Zi show 子类有直接使用子类
		}
	}  
```

```java
A:方法覆盖的注意事项 a:权限:子类方法覆盖父类方法，必须要保证权限大于等于父类权限。 四大权限:public>默认=protected>private   
class Fu{
		void show(){

		}
		public void method(){

		}
    }
    class Zi() extends Fu{
		public void show(){//编译运行没问题

		}  
		void method(){//编译错误

	    }   
    }
 b:方法定义:子类方法和要重写的父类的方法:方法的方法名和参数列表都要一样。
   关于方法的返回值:
     如果是基本数据类型,子类的方法和重写的父类的方法返回值类型必须相同
     如果是引用数据类型,子类的方法和重写的父类的方法返回值类型可以相同或者子类方法的返回值类型是父类方法返回值类型的子类
     class Fu{
		int show(){

		}
		public Fu method(){

		}

		public Fu method2(){

		}

    }
    class Zi() extends Fu{
		public int show(){//返回值为基本类型的重写

		}  
		public Fu method(){//子类的方法和重写的父类的方法返回值类型可以相同

	    }   
	    public Zi method2(){//子类方法的返回值类型是父类方法返回值类型的子类

	    }   
    }
 c:重载与重写对比:
    重载:
	    权限修饰符(public private 默认):无关
	    方法名:重载的两个方法的方法名必须相同
	    形参列表:
	      形参类型的顺序不同
	      形参的个数不同
	      形参的类型不同
	      三者至少满足一个
	    返回值类型:
	      重载与返回值类型无关
	重写:
	    权限修饰符(public private 默认): 
	      子类方法的权限>=父类的方法的权限
	    方法名: 
	      子类方法和父类方法必须相同
	    形参列表: 
	       子类方法和父类方法的形参列表必须相同
	    返回值类型:
	      基本类数据类型:
	        必须相同
	      引用数据类型:
	       子类方法的返回值类型和父类方法的返回值类型相同
	       或者
	       子类方法的返回值类型是父类方法的返回值类型的 子类
```

##### 多态

现实事物经常会体现出多种形态，如学生，学生是人的一种，则一个具体的同学张三既是学生也是人，即出现两种形态。Java作为面向对象的语言，同样可以描述一个事物的多种形态。如Student类继承了Person类，一个Student的对象便既是Student，又是Person。

父类类型  变量名 = new 子类类型();

```java
* A: 掌握了多态的基本使用后，那么多态出现后类的成员有啥变化呢？前面学习继承时，我们知道子父类之间成员变量有了自己的特定变化，
	* 那么当多态出现后，成员变量在使用上有没有变化呢？
	* 多态出现后会导致子父类中的成员变量有微弱的变化


* B: 代码演示
	class Fu {
		int num = 4;
	}
	class Zi extends Fu {
		int num = 5;
	}
	class Demo {
		public static void main(String[] args) 	{
			Fu f = new Zi();
			System.out.println(f.num);
			Zi z = new Zi();
			System.out.println(z.num);
		}
	}

* C: 多态成员变量
	当子父类中出现同名的成员变量时，多态调用该变量时：
	编译时期：参考的是引用型变量所属的类中是否有被调用的成员变量。没有，编译失败。
	运行时期：也是调用引用型变量所属的类中的成员变量。
	简单记：编译和运行都参考等号的左边。编译运行看左边。

* D: 多态出现后会导致子父类中的成员方法有微弱的变化。看如下代码
	class Fu {
		int num = 4;
		void show()	{
			System.out.println("Fu show num");
		}
	}
	class Zi extends Fu {
		int num = 5;
		void show()	{
			System.out.println("Zi show num");
		}
	}
	class Demo {
		public static void main(String[] args) 	{
			Fu f = new Zi();
			f.show();
		}
	}

* E: 多态成员方法
	编译时期：参考引用变量所属的类，如果没有类中没有调用的方法，编译失败。
	运行时期：参考引用变量所指的对象所属的类，并运行对象所属类中的成员方法。
	简而言之：编译看左边，运行看右边。
```

```java
B: 向上转型：当有子类对象赋值给一个父类引用时，便是向上转型，多态本身就是向上转型的过程。
	使用格式：
	父类类型  变量名 = new 子类类型();
	如：Person p = new Student();
* A: 向下转型：一个已经向上转型的子类对象可以使用强制类型转换的格式，将父类引用转为子类引用，这个过程是向下转型。如果是直接创建父类对象，是无法向下转型的！
	使用格式：
	子类类型 变量名 = (子类类型) 父类类型的变量;
	如:Student stu = (Student) p;  //变量p 实际上指向Student对象
```

#### 抽象类和接口

```java

a:抽象类一定是个父类？ 是的，因为不断抽取而来的。 
b:抽象类中是否可以不定义抽象方法? 是可以的
A:抽象方法定义的格式：
   a:public abstract 返回值类型 方法名(参数);
     抽象类定义的格式：
	 abstract class 类名 {

	  }
    b:抽象类示例代码：
	   /*
		 *  定义类开发工程师类
		 *    EE开发工程师 :  工作
		 *    Android开发工程师 : 工作
		 *  
		 *    根据共性进行抽取,然后形成一个父类Develop
		 *    定义方法,工作: 怎么工作,具体干什么呀
		 *  
		 *    抽象类,不能实例化对象, 不能new的
		 *    不能创建对象的原因:  如果真的让你new了, 对象.调用抽象方法,抽象方法没有主体,根本就不能运行
		 *    抽象类使用: 定义类继承抽象类,将抽象方法进行重写,创建子类的对象
		 */
		public abstract class Develop {
		   //定义方法工作方法,但是怎么工作,说不清楚了,讲不明白
			//就不说, 方法没有主体的方法,必须使用关键字abstract修饰
			//抽象的方法,必须存在于抽象的类中,类也必须用abstract修饰
			public abstract void work();
		}

*/ public abstract class Animal { public void sleep(){ System.out.println("动物睡觉"); }

	}
	public class Cat extends Animal{

    }   
  
    public class Test {
		public static void main(String[] args) {
			//Cat c = new Cat();
			new Cat().sleep();//不让该类创建对象,方法可以直接让子类去使用
		}
    }
 c:抽象关键字abstract不可以和哪些关键字共存？
  1:private：私有的方法子类是无法继承到的，也不存在覆盖，
             而abstract和private一起使用修饰方法，abstract既要子类去实现这个方法,
             而private修饰子类根本无法得到父类这个方法。互相矛盾。 
  
    /*
	 *   抽象类,可以没有抽象方法,可以定义带有方法体的方法
	 *   让子类继承后,可以直接使用
	 */
	public  abstract class Animal {
	 
	     // private abstract void show();
	     //抽象方法,需要子类重写, 如果父类方法是私有的,子类继承不了,也就没有了重写
	}
```

##### 接口

接口只描述所应该具备的方法，并没有具体实现，具体的实现由接口的实现类(相当于接口的子类)来完成。这样将功能的定义与实现分离，优化了程序设计。

接口中可以定义变量，但是变量必须有固定的修饰符修饰，public static final 所以接口中的变量也称之为常量，其值不能改变。

```java
interface Demo { ///定义一个名称为Demo的接口。
			public abstract void show1();
			public abstract void show2();
		}

		//定义子类去覆盖接口中的方法。类与接口之间的关系是 实现。通过 关键字 implements
		class DemoImpl implements Demo { //子类实现Demo接口。
			//重写接口中的方法。
			public void show1(){}
			public void show2(){}
		}
```

一个类如果是实现类,有两种操作方法:
   第一:实现类是非抽象类,就需要重写接口中所有的抽象方法.
   第二:实现类也声明为抽象类,那么实现类可以不重写接口中的抽象方法。

一个实现类可以多实现接口，但是不能多继承。一个实现类可以在实现接口的同时继承类* A: 向下转型：一个已经向上转型的子类对象可以使用强制类型转换的格式，将父类引用转为子类引用，这个过程是向下转型。如果是直接创建父类对象，是无法向下转型的！

    使用格式：
	子类类型 变量名 = (子类类型) 父类类型的变量;
	如:Student stu = (Student) p;  //变量p 实际上指向Student对象

##### final

```java
final修饰类不可以被继承，但是可以继承其他类。
final修饰的方法不可以被覆盖,但父类中没有被final修饰方法，子类覆盖后可以加final。
final修饰的变量称为常量，这些变量只能赋值一次
修饰成员变量，需要在创建对象前赋值，否则报错。(当没有显式赋值时，多个构造方法的均需要为其赋值。
```

##### static

```java
* A：特点1:
		被static修饰的成员变量属于类，不属于这个类的某个对象。
		（也就是说，多个对象在访问或修改static修饰的成员变量时，其中一个对象将static成员变量值进行了修改，
		其他对象中的static成员变量值跟着改变，即多个对象共享同一个static成员变量）
* B: 代码演示
		class Demo {
			public static int num = 100;
		}

		class Test {
			public static void main(String[] args) {
				Demo d1 = new Demo();
				Demo d2 = new Demo();
				d1.num = 200;
				System.out.println(d1.num); //结果为200
				System.out.println(d2.num); //结果为200
			}
		}

* A: 注意事项
		被static修饰的成员可以并且建议通过类名直接访问。

* B: 访问静态成员的格式：
		类名.静态成员变量名
		类名.静态成员方法名(参数)
		对象名.静态成员变量名     		------不建议使用该方式，会出现警告
		对象名.静态成员方法名(参数) 	------不建议使用该方式，会出现警告

* C: 代码演示
		class Demo {
			//静态成员变量
			public static int num = 100;
			//静态方法
			public static void method(){
				System.out.println("静态方法");
			}
		}
		class Test {
			public static void main(String[] args) {
				System.out.println(Demo.num);
				Demo.method();
			}
		}
```

#### 异常

Java代码在运行时期发生的问题就是异常。

```java
Throwable: 它是所有错误与异常的超类（祖宗类）
		|- Error 错误
		|- Exception 编译期异常,进行编译JAVA程序时出现的问题
			|- RuntimeException 运行期异常, JAVA程序运行过程中出现的问题
```

```java
A: 声明
	* 将问题标识出来，报告给调用者。如果方法内通过throw抛出了编译时异常，而没有捕获处理（稍后讲解该方式），那么必须通过throws进行声明，让调用者去处理。
* B: 声明异常格式
	* 修饰符 返回值类型 方法名(参数) throws 异常类名1,异常类名2… {   }
* C：注意事项：
	* throws用于进行异常类的声明，若该方法可能有多种异常情况产生，那么在throws后面可以写多个异常类，用逗号隔开。
try {
		//需要被检测的语句。
	}
	catch(异常类 变量) { //参数。
		//异常的处理语句。
	}
	finally {
		//一定会被执行的语句。
	}
* C: 格式说明
	* a: try
		* 该代码块中编写可能产生异常的代码。
	* b: catch
		* 用来进行某种异常的捕获，实现对捕获到的异常进行处理。
	* c: finally：
		* 有一些特定的代码无论异常是否发生，都需要执行。
		* 另外，因为异常会引发程序跳转，导致有些语句执行不到。
		* 而finally就是解决这个问题的，在finally代码块中存放的代码都是一定会被执行的。
	* d：try...catch...处理掉异常后，程序可以继续执行
```

#### 多线程

##### 线程和进程区别

* 程序由指令和数据组成，但这些指令要运行，数据要读写，就必须将指令加载至 CPU，数据加载至内存。在指令运行过程中还需要用到磁盘、网络等设备。进程就是用来加载指令、管理内存、管理 IO 的。
* 当一个程序被运行，从磁盘加载这个程序的代码至内存，这时就开启了一个进程。
* 一个进程之内可以分为一到多个线程。
* 一个线程就是一个指令流，将指令流中的一条条指令以一定的顺序交给 CPU 执行 。

#### JVM

程序计数器：记录下一条jvm指令（字节码）的内存地址

- 线程私有，不会存在内存溢出的区域

栈：线程运行需要的内存空间

- 栈祯：栈内存的每一个元素（每个方法运行时需要的内存）
- 每个线程只能有一个活动栈祯，也就是该线程正在执行的方法
- 方法内局部变量是否线程安全？如果方法内局部变量没有逃离方法的作用范围，是线程安全的。
- 内存溢出，栈祯过多，栈祯过大（stackoverflow）

本地方法栈：不是用java编写的方法，主要用来与操作系统底层打交道。

- Java通过本地方法接口来调用这些方法，而调用这些本地方法时所需要的栈内存空间就是本地方法栈。

堆内存

- 简单理解是通过new 关键字创建的对象是堆内存
- 特点：线程共享，垃圾回收机制

方法区：

- 存储已经加载的类型信息、常量池、静态变量、即时编译后的代码

- 常量池：虚拟机指令根据这张表找到要执行的类名，方法名，参数类型，字面量

- 运行时常量池：当该类被加载的时候，把该类的常量池信息放入运行时常量池（内存）

#### 垃圾回收

##### 如何判断垃圾可以回收？

- 引用计数法：给一个对象定义一个引用计数器，每当该对象被引用一次引用计数器就加1，如果一个对象的引用计数器为0，则说明这个对象已死
- 可达性分析算法：扫描堆中的对象，看能否沿着GC root 对象为起点的引用链找到该对象，找不到，表示可以回收。

##### 垃圾回收算法

- 标记清除算法：标记垃圾并清除 速度快，但会造成内存碎片
- 标记整理算法：标记垃圾后整理“拼接"非垃圾区域 速度慢，但没有内存碎片
- 复制算法：from和to两块区域，from标记垃圾后，将非垃圾区域复制到to，直接清除整个from区域，再交换from和to区域 不会有内存碎片，但需要双倍内存空间

##### 分代回收算法

- 对象首先分配在伊甸园区域
- 新生代空间不足时，触发minor gc，伊甸园和from存活的对象使用copy复制到to中，存活的对象年龄加1并且交换from和to
- minor gc会引发stop the world， 暂停其他用户的进程，等垃圾回收结束，用户线程才恢复运行
- 当对象寿命超过阈值时，会晋升至老年代
- 当老年代空间不足，会先尝试触发minor gc，如果之后空间仍不足，那么触发full gc

#### 类加载过程

##### 加载过程

- 通过一个类的全限定名获取定义此类的二进制字节流（找到在磁盘上的.class文件）
- 将这个字节流所代表的静态存储结构转化为方法区的运行数据结构（C++的instanceKlass）
- 在内存中生成一个代表这个类的java.lang.class对象，作为方法区这个类的各种数据的访问入口（在堆内存中生成class对象作为接口）

##### 连接过程

- 验证：确保class文件中的字节流信息符合要求，不会危害虚拟机自身安全。
- 准备：正式为类中定义的变量分配内存并设置类变量初始值的阶段（static修饰的变量）
- 解析：将常量池中的符号引用解析为直接引用（把其他类的具体信息ex内存地址加载到常量池中）（符号引用仅仅是个符号，并不知道类或者方法或者属性具体的内存位置）

##### 初始化

初始化阶段，根据程序编码制定的主观计划去初始化类变量和其他资源

##### 双亲委派模型：

如果一个类加载器收到了类加载的请求，它首先不会自己去尝试加载这个类，而是把这个请求委派给父类加载器去完成。

- Bootstrap Class Loader
- Extension Class Loader

##### Java 线程安全

- 线程使用共享数据时，都是先从主内存中拷贝到工作内存，使用完成之后再写入主内存，可以理解为线程之间通讯是通过共享内存的方式实现的。

原子性：

- 访问某个共享变量的操作从其他线程来看，要么已经执行完毕，要么尚未发生，即其他线程看不到中间结果，访问同一组共享变量的原子操作不能够交错
- 有两种实现方式：锁，处理器的CAS指令
- 锁具有排它性，保证共享变量在某一时刻只能被一个线程访问
- CAS直接在硬件（处理器和内存）层次上实现，看作是硬件锁
- CAS 操作包含三个操作数内存位置（V）、预期原值（A）和新值(B)。执行CAS操作的时候，将内存位置的值与预期原值比较，如果相匹配，那么处理器会自动将该位置值更新为新值。否则，处理器不做任何操作。

可见性：

- 在多线程环境中，一个线程对共享变量进行更新之后，后续其他的线程可能无法立即读取到这个更新的结果。
- Volatile 关键字：保证线程修改完变量立即写回主存，而且每个线程在使用变量前必须从主存刷新数据
- 禁止指令的重排序

互斥同步：同步是指在多个线程并发访问共享数据时，保证共享数据在同一个时刻只被一个（或者是一些，使用信号量的时候）线程使用。

非阻塞同步：通俗的说，就是先进性操作，如果没有其他线程争用共享数据，那操作就成功了，如果共享数据有争用，产生了冲突，那就再采取补偿措施（最常见的补偿措施就是不断的重试，直到成功为止），这种乐观的并发策略不需要把线程挂起，因此这种同步操作称为非阻同步。
