# 高级教程
## 一、数据结构
### （1）枚举（Enumeration）
一次获得一个对象集合中的元素。现在用得少了，被迭代器取代。
```java
        Enumeration vEnum = v.elements();
        while(vEnum.hasMoreElements()){
            System.out.print(vEnum.nextElement() + " ");
        }
```
### （2）位集合（BitSet）
1. BitSet类：用数组保存位值（注：print时，显示true位的索引）
2. 初始化：`BitSet(int size)`，不写就默认64位。无论输入多少，size会变成64的倍数（为了内存对齐）。最初大家都是false。
   ```java
   BitSet bits1 = new BitSet(64);
   ```
3. 常用方法：
   1. 大小：
      * `size()`：容量，能存bit数
      * `length()`：逻辑大小，最高位索引+1
   2. 设置bit位
      * `void set(int index,boolean v)`：把某一位（0开始）置为true/false（不写v，默认true）
      * `void set(int startIndex, int endIndex, boolean v)`：start到end-1置位true/false（不写v，默认true）
      * `void clear(int index)`：将某一位置为false
   3. 读取：
      * `boolean get(int index)`
      * `BitSet get(int startIndex, int endIndex)`
      * `int nextSetBit(int startIndex)`：从start开始，第一个true的索引
      * `int nextClearBit(int startIndex)`：从start开始，第一个false的索引
   4. 运算：and，or，xor
      * 例：`b1.and(b2);`，结果存在b1里面
### （3）向量（Vector）
1. Vector类：动态数组，同步访问，线程安全。一个Vector可以装类型不同的对象。
   1. `import java.util.*;`  
   2. `Vector(int size)`：指定容量capacity()，不写默认为10  
   3. `Vector(int size,int incr)`：增量incr表示超过容量时，容量每次+incr
   4. `Vector(Collection c)`：创建一个包含集合c的向量  
2. 常用方法：
   1. 增加元素：
      * `void addElement(Object obj)`：添加到末尾，且size()+1
      * `void add(int index, Object element)`：在某个位置插入一个元素（不能中间空位置跳着插）
   2. 移除元素
      * 清除所有元素：clear
      * 删除第一个匹配项  
        * `boolean remove(Object obj)`  
        * `boolean removeElement(Object obj) `  
      * 删除指定位置元素：
        * `Object remove(int index)`
        * `void removeElementAt(int index) `
   3. `get()`，`clone()`，`contains()`，`indexOf(Object elem)`与其他的相同
   4. `elements()`返回一个Enumeration类型的对象，方便遍历
### （4）栈（Stack）
1. Stack是Vector的子类，先进后出
   ```java
   Stack<Integer> st = new Stack<Integer>();
   ```
2. 常用方法：
   * 查看是否为空：`boolean empty()`
   * 查看栈顶元素（不移除）：`Object peek( )`
   * 出栈（pop），移除栈顶元素：`Object pop( )`或者`showpop`
   * 入栈（push），元素压入栈顶：`Object push(Object element)`或者`show push`
   * 返回对象位置（1为基数）：`int search(Object element)`
3. 空栈错误：EmptyStackException
   ```java
   try {
        showpop(st);
    } catch (EmptyStackException e) {
        System.out.println("empty stack");
    }
   ```
### （5）字典（Dictionary）
1. Dictionary是一个抽象类，用来存储键/值对。（已过时，用Map接口代替）
2. Map接口：HashMap 是 Map 接口的实现，非线程安全
   1. 初始化：`Map m1 = new HashMap();` 
   2. 将某值与某键关联:`m1.put("Zara", "8");`
   3. 返回某键的值：`Object get(Object k)`
### （6）哈希表（Hashtable）
1. Hashtable继承自Dictionary，且实现了Map接口。Hashtable和HashMap类很相似，但是它支持同步。
2. 初始化
   1. `Hashtable(int size,float fillRatio)`：fillRatio指定填充比例（0~1），两个参数不写就默认。
   2. `Hashtable(map m)`：创建了一个以M中元素为初始化元素的哈希表，哈希表的容量被设置为M的两倍。
3. 常用方法
   1. 新增键值对：`Object put(Object key, Object value)`
   2. 由键得值`Object get(Object key)`
   3. 查是否存在（k与v）：`boolean contains(Object value`)==`containsValue(Object value)`，`containsKey(Object key)`
   4. 枚举：`Enumeration keys()`键的枚举，`Enumeration elements()`值的枚举
   5. 增加此哈希表的容量并在内部对其进行重组：`void rehash()`
### （7）属性（Properties）
1. Properties 继承于 Hashtable，键和对应值都是字符串
2. 初始化：Properties capitals = new Properties();
3. 常用方法：
   1. 新增键值对（put）：`Object setProperty(String key, String value)`（也可以用put，但不建议）
   2. 由键得值（get）：`String getProperty(String key)`
## 二、集合框架
### （一）Java集合框架
Java 集合框架主要包括两种类型的容器：一种是集合（Collection），存储一个元素集合。另一种是图（Map），存储键/值对映射。  
集合框架都在java.util包里面。
1. Collection 接口：存储一组不唯一，无序的对象
   1. List 接口：存储一组不唯一，有序的对象（有index）
      1. ArrayList类：可变大小数组，随机访问和遍历元素时性能好，插入删除效率低。
      2. LinkedList类：允许有null，查找效率低。
      3. Vector——>Stack
   2. Set 接口：Set 接口存储一组唯一，无序的对象（无重复元素）
      1. HashSet类：唯一，无序，允许null。
2. Map接口：存储一组键值对象，提供key（键）到value（值）的映射
   1. HashMap类：散列表，存储键值对(key-value)映射。无序。最多一个key为null。
### （二）集合实现类
1. ArrayList动态数组：可以动态修改的数组。里面的元素都是（同一种）对象。
   1. 初始化：`ArrayList<E> objectName =new ArrayList<>()`
   2. 常用方法：添加add("name1")，访问get(0)，修改set(1,"name2"),删除remove(2),大小size()
   3. 排序（数字或者字母）：`Collections.sort(sites);` 
2. LinkedList链表
   1. 初始化：`LinkedList<E> list = new LinkedList<E>();`
   2. 常用方法：add、remove、get和ArrayList相同，但链表有更高效的方法。
      1. 在开头/结尾插入：`addFirst/addLast(name1)`
      2. 在开头/结尾插入：`removeFirst/removeLast(name2)`
      3. 得到开头/结尾元素：`getFirst/getLast()`
3. HashSet：重复的添加无效
   1. 初始化：`HashSet<String> sites = new HashSet<String>();`
   2. 常用方法：add，contains，remove，size
4. HashMap： key 与 value 类型可以不同
   1. 初始化（<key,value>）：`HashMap<Integer, String> Sites = new HashMap<Integer, String>();`
   2. 常用方法：
      1. 添加键值对：`put(key,value)`
      2. 由键得值：`get(key)`
      3. 删除元素：`remove(key)`
      4. 只要key（迭代时用，增强for循环）：`keySet()`。只要value：`values()` 
### （三）迭代器和比较器
1. 迭代器：Iterator类
   1. 初始化（sites是个Vector）：`Iterator<String> it = sites.iterator();`
   2. 迭代：
      ```java
      while(it.hasNext()) {
         System.out.println(it.next());
      }
      ```
   3. 删除元素：`it.remove()`
2. 比较器：
   1. Comparable接口：需要实现这个接口，重写compareTo()方法
      ```java
      //比较名字
      public class Student implements Comparable<Student> {
         @Override
         public int compareTo(Student o) {
            return this.getName().compareTo(o.getName());
         }
      }
      ```
   2. Comparator接口：需要实现这个接口，重写compare()方法。重写之后直接用sort排序，就能比较。
      ```java
      //年龄比较器
      class AgeComparator implements Comparator<Student> {
         @Override
         public int compare(Student o1, Student o2) {
            if (o1.getAge() > o2.getAge()) {
                  return 1;
            } else if (o1.getAge() < o2.getAge()) {
                  return -1;
            } else {
                  return 0;
            }
         }
      }
      //名字比较器
      class NameComparator implements Comparator<Student> {
         @Override
         public int compare(Student o1, Student o2) {
         return o1.getName().compareTo(o2.getName());
         }
      }
      ```
      * 补充：使用`Arrays.asList()`将数组转换为一个List集合。
      ```java
      String[] s = {"name1","name2","name3"};
      List<String> myList = Arrays.asList(s);
      //两种排序
      Arrays.sort(s);
      Collections.sort(myList);
      ```
   3. lambda表达式（Java8之后）
## 三、泛型
1. 泛型方法:可以接收不同类型的参数  
    ```java
    //定义
    public static <E> void printArray( E[] inputArray )
    //调用
    Integer[] intArray = { 1, 2, 3, 4, 5 };
    Double[] doubleArray = { 1.1, 2.2, 3.3, 4.4 };
    printArray( intArray  ); // 传递一个整型数组
    printArray( doubleArray );// 传递一个双精度型数组
    ```
2. 泛型类（使用最多）:可以有没确定类型的成员
    ```java
    public class Box<T> {
        private T t;
        //运用
        Box<Integer> integerBox = new Box<Integer>();
        Box<String> stringBox = new Box<String>();
    }
    ```
3. 限制泛型可用类型：泛型的类型必须实现或者继承List类（eg.）
   ```java
   public class LimitClass<T extends List>{
       public static void main(String[] args){
           LimitClass<ArrayList> l1 = new LimitClass<ArrayList>();
           LimitClass<LinkedList> l2 = new LimitClass<LinkedList>();
       }
   }
   ```
4. 类型通配符：用？代替具体的类型参数。例如：List<?> 在逻辑上是List<String>,List<Integer> 等的父类
   ```java
   public static void getData(List<?> data) {
       System.out.println("data :" + data.get(0));
   }
   //使用时
    List<String> name = new ArrayList<String>();
    List<Integer> age = new ArrayList<Integer>();
    List<Number> number = new ArrayList<Number>();

    name.add("icon");
    age.add(18);
    number.add(314);

    //类型通配符上限，表示：接受Number及其下层子类类型（这时输入String就不行）。
    public static void getUperNumber(List<? extends Number> data) {
        System.out.println("data :" + data.get(0));
    }
    //类型通配符下限，表示：接受Number及其上层父类类型。
      List<? super Number>
   ```
## 四、序列化
1. 序列化（ObjectOutputStream类）：把一个对象表示为一个字节序列（.ser）。
   ```java
   FileOutputStream fileOut =new FileOutputStream("/tmp/employee.ser");
   ObjectOutputStream out = new ObjectOutputStream(fileOut);
   out.writeObject(e);
   out.close();
   fileOut.close();
   ```
2. 反序列化（ObjectInputStream类）：用写入文件的序列化对象（.ser）新建对象。
   ```java
   FileInputStream fileIn = new FileInputStream("/tmp/employee.ser");
   ObjectInputStream in = new ObjectInputStream(fileIn);
   e = (Employee) in.readObject();
   in.close();
   fileIn.close();
   ```
3. 一个类的对象要想序列化成功，必须满足：
   1. 该类必须实现 java.io.Serializable 接口。
   2. 该类的所有属性必须是可序列化的。如果有一个属性不是可序列化的，则该属性必须注明是短暂（transient）的。
## 五、多线程编程
Java 提供了三种创建线程的方法：
1. 实现 Runnable 接口
2. 继承 Thread 类本身
3. 通过 Callable 和 Future 创建线程