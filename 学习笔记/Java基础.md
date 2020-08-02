# 基础教程
## 一、面向对象编程
### 1. 简介
1. 类：`public class Puppy {属性，方法}`   
2. 属性：在前面定义，全局变量，类里面能用  
3. 构造方法：`public Puppy(String name, int x,int y){}`
* 构造方法没有返回值
* 构造方法的名称必须与类同名，一个类可以有多个构造方法）
* 默认构造方法的访问修改符和类的访问修改符相同
4. 方法：`public void（或int） setAge( int age ){return}`
5. 主方法，创建对象（new）：
    ```java
    public static void main(String[] args){ 
    Puppy myPuppy = new Puppy( "tommy" ,1,2); 
    myPuppy.setAge( 2 );
    System.out.println("变量值 : " + myPuppy.puppyAge );
    }
    ```
    注：System.out.println是换行输出，System.out.print是一般输出

### 2. 注意
1. 源文件：
（1）一个源文件中有一个 public 类，多个非 public 类（class定义的类只有包内访问权限）
（2）源文件的名称应该和 public 类的类名保持一致
（3）先package，再import，这两个对源文件中所有类都有效
2. 对象和对象引用：Puppy myPuppy = new Puppy();
则myPuppy是对象引用，new Puppy（）是创建了一个对象。这句话的意思是把创建的对象用myPuppy来引用。（一个对象可以被多次引用，之前的引用被回收）
3. 方法
   1. 静态方法（static修饰）：在外部调用静态方法时，可以使用"类名.方法名"的方式，也可以使用"对象名.方法名"的方式。而实例方法只有后面这种方式。也就是说，调用静态方法可以无需创建对象。
   2. 方法重载：两个方法（包括构造方法）名字一样，但是参数列表不一样（必须不一样）。Java编译器会判断哪个该被调用。
   3. 可变参数：一个方法只能有一个可变参数，且必须在最后。  
   `public static void printMax( double... numbers) {}`
   4. 类和成员的权限：类的权限会约束成员的权限。  
   * 内部类：四种修饰都可以。  
   * 外部类：只能public和默认。
   5. 静态变量和静态方法（static）：类名.静态成员（不建议用：对象.静态成员）。
   *  静态方法中不用this关键字（主方法也是静态方法）。静态方法中不可以直接调用非静态方法。
   * 静态变量：不同对象的静态变量对应同一片内存区域，可以更改。
   6. 对象的比较：==：比较引用。.equals()：比较内容

## 二、基础语法
### 2.1 基础数据类型
1. 内置数据类型（有符号二进制补码）
* byte：8位 ——> -128~127（$-2^7$~$2^7-1$）  
* short：16位 ——>-32768~32767（$-2^{15}$~$2^{15}-1$）  
* int（整数默认）：32位 ——>（$-2^{31}$~$2^{31}-1$）  
* long（定义时后面加L，否则要溢出）：64位 ——>    
* float：单精度，32位，定义时后面加f或F
* double：双精度，64位
* boolean：一位，true 和 false
* char：16位Unicode（\u0000~\uffff）（可以直接赋数字，也可以加单引号赋字符）

补充：
* 补码：10000000做最小的负数（因为它等于（-1）+（-127））
* 科学计数法：3.13E3，3.14E-3
* 0144表示8进制，0x64表示16进制

2. 引用数据类型：类似于指针，默认是null。  
`Site site = new Site("Runoob")`  
这个site就是个引用变量，给它赋值为new Site（“Runoob”）生成的对象

3. Java常量（final，通常大写字母表示，声明时必须赋值）
`final double PI = 3.1415927;`  
转义字符：\n，\r，\t，\’，\’’，\\，\123（八进制），\u0052（十六进制）  
\r：return到当前行的最左边  
\n：newline向下移动一行，并不移动左右

4. 类型转换（boolean不能转换）：
   1. 自动转换（运算中：低级向高级转）:  
    byte,short,char—> int —> long—> float —> double(低到高)
   2. 强制转换（高级向低级必须用强制）  
    int i1 = 123;  
    byte b = (byte)i1;
### 2.2 变量类型
1. 变量类型（类变量和实例变量称为成员变量）
   1. 类变量（静态变量）：独立于方法之外的变量，用 static 修饰。可以跨类，以“类名.静态变量”在其他类使用。
   2. 实例变量：独立于方法之外的变量，不过没有 static 修饰。
   3. 局部变量：类的方法中的变量。方法调用完成后被销毁，必须初始化。在方法里，若成员变量和局部变量重名，隐藏成员变量。


# 面向对象
## 枚举类（enum）
```java
enum Color { RED, GREEN, BLUE;} 
Color c1 = Color.RED;
```
* 可声明在内部（内部类）
* 所有的枚举值都是 public static final
* 构造函数只能使用 private 访问修饰符

方法：
1. values() 返回枚举类中所有的值。Color arr[] = Color.values();
2. ordinal()方法可以找到每个枚举常量的索引，就像数组索引一样。Color col；col.ordinal()
3. valueOf()方法返回指定字符串值的枚举常量。Color.valueOf("RED")
## 包（package）
import关键字  
```java
package payroll; 
import payroll.*;
```
类名 -> vehicle.Car  
路径名 -> vehicle\Car.java(Windows系统)  
编译的时候会创建一个输出文件.class  
类.class文件可以和源码.java分开放