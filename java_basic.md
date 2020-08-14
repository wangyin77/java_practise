# Java 基础
## HelloWorld
1. `java -version` 查看版本
2. `javac filename.java` 编译
3. `java classname` 运行(不带.class)
4. `public static void main(String[] args)` 主方法
5. `public class HelloWorld` 一个可以公开访问的类(类的第一个字母大写)
6. `System.out.println("hello world");` 控制台输出
## 面向对象
7. 属性是变量,属性的类型可以是基本类型,也可以是类类型(String)
8. speed为方法的参数
    ```java
    public class Hero 
        void addSpeed(int speed)
            moveSpeed = moveSpeed + speed;
    ```
9. 方法一般以动词开头(addSpeed)
## 变量
10. 基本变量类型：整型(byte/short/int/long)、字符型(char)、浮点型(float/double默认)、布尔型(boolean不能用01赋值)
11. String是类类型，不可改变，类似常量
12. 字面值，给基本类型的变量赋值
13. 变量命名规则：只能使用字母 数字 $ _，第一个字符 不能使用数字
14. final修饰后只能赋值一次
15. 从{开始，到对应的} 结束为一个块
## 操作符
16. 从控制台输入数据
    ```java
    import java.util.Scanner;
    public class HelloWorld 
        public static void main(String[] args) {
            Scanner s = new Scanner(System.in);
            String a = s.nextLine();
            System.out.println("读取的字符串是："+a);
        }
    ```
17. 逻辑：& 长路(两边都会执行) && 短路 |长路 || 短路 ! ^
18. 整数转二进制：`Integer.toBinaryString(i)`
19. 位与 & 位或 | 异或 ^ 非 ! 左移 << 右移 >> 
## 控制流程
20. 使用boolean变量结束外部循环
    ```java
    boolean breakout = false; //是否终止外部循环的标记
	for (int i = 0; i < 10; i++) 
		for (int j = 0; j < 10; j++) 
			breakout = true; break; //终止外部循环的标记设置为true
		if (breakout) break; //判断是否终止外部循环
    ```
21. 使用标签结束外部循环
    ```java
    outloop: //outloop这个标示是可以自定义的
    for (int i = 0; i < 10; i++) 
        for (int j = 0; j < 10; j++) 
            break outloop; //结束外部循环
    ```
## 数组
22. `int[] a = new int[5];`创建一个数组，长度不可变
23. `a.length` 长度n(0..n-1)
24. `(int) (Math.random() * 100)`0-100的随机整数
25. 初始化：`int[] a = new int[]{100,102,444,836,3236};` 或`int[] a = {100,102,444,836,3236};`
26. 增强型for：`for (int each : values) `
27. `System.arraycopy(src, srcPos, dest, destPos, length)` 复制数组(src: 源数组, dest: 目标数组, pos起点)
28. 二维：`int[][] a = new int[2][3];`
### Array工具类
29. `import java.util.Arrays;`
30. `copyOfRange(int[] original, int from, int to)`复制数组,第三个参数表示结束位置(取不到)
31. `String content = Arrays.toString(a);`转换为字符串
32. `Arrays.sort(a);`数组排序
33. `Arrays.binarySearch(a, 62);`查找62，必须先排序
34. `Arrays.equals(a, b)` 判断是否相同
35. `Arrays.fill(a, 5);`填充
## 类和对象
36. 如果一个变量的类型是 类类型，而非基本类型，那么该变量又叫做引用；引用有多个，但是对象只有一个。
37. `public class A extends B`类继承
38. 方法的重载指的是方法名一样，但是参数类型不一样
39. 可变数量的参数方法
    ```java
    public void attack(Hero... heros) 
        for (int i = 0; i < heros.length; i++) 
            System.out.println(name + " 攻击了 " + heros[i].name);
    ```
40. 通过一个类创建一个对象，这个过程叫做实例化,实例化是通过调用构造方法(又叫做构造器)实现的.
41. 定义了有参的构造方法，默认的无参的构造方法就失效了
42. 构造方法可以重载
43. this代表当前对象
44. 重名时，在方法体中，只能访问到参数name，通过this关键字可以访问对象的属性
    ```java
    public void setName3(String name)
        this.name = name;//name代表的是参数name,this.name代表的是属性name
    ```
45. 在一个构造方法中，调用另一个构造方法，可以使用this()
    ```java    
    public Hero(String name)//带一个参数的构造方法
        this.name = name;      
    public Hero(String name,float hp)//带两个参数的构造方法
        this(name); this.hp = hp;
    ```
46. 在方法中，使参数引用指向一个新的对象，不会改变方法外引用的指向(传参不会改变原来的引用,h类似一个临时变量出去就被销毁了)
    ```java
    public void revive(Hero h)
        h = new Hero("提莫",383);
    ```
47. `import property.Weapon;`使用其他包下的类，必须import
48. 成员变量有四种修饰符:private 私有的、protected 受保护的、public 公共的、(package/friendly/default 不写)

    |修饰符|自身|同包子类|同包类|不同包子类|其他类|
    |:---:|:---:|:---:|:---:|:---:|:---:|
    |private|√|×|×|×|×|
    |package|√|√|√|×|×|
    |protected|√|√|√|√|×|
    |public |√|√|√|√|√|
49. 属性用private，调用用public，会被子类继承用protected，作用范围最小原则
50. static修饰类属性，又叫做静态属性
51. 如果一个属性每个对象都不一样，应当设计为对象属性，反之应设计为类属性
52. 类方法,又叫做静态方法,static修饰; 对象方法,又叫实例方法，非静态方法
53. 访问类方法，不需要对象的存在
54. 如果一个方法，没有调用任何对象属性，那么就可以考虑设计为类方法
55. 对象属性初始化有3种:
    1. 声明该属性的时候初始化
    2. 构造方法中初始化
    3. 初始化块,`{}`括起来就行
56. 类属性初始化有2种
    1. 声明该属性的时候初始化
    2. 静态初始化块
    ```java
    static{
        itemCapacity = 6;//静态初始化块 初始化
    }
    ```
57. 优先级：属性声明->初始化块->构造方法。当对一个对象实例化时，首先会加载实例变量，然后再执行初始化代码块，最后执行构造方法。
    ```java
    public class HeroTest {
        public String name = "some hero"; System.out.println("声明");
        public HeroTest(){
            name = "one hero"; System.out.println("构造方法");
        }
        {
            name = "the hero"; System.out.println("块");
        }            
        public static void main(String[] args) {
            HeroTest ht = new HeroTest();
            System.out.println(ht.name);
        }
    }
    Output：声明 块 构造方法 one hero
    ```
58. 单例模式又叫做 Singleton模式，指的是一个类，在一个JVM里，只有一个实例存在。
59. 有两种实现方式：饿汉or懒汉。流程都是将构造方法私有化，让一个静态属性指向实例，给一个public static方法返回这个静态属性。饿汉初始化静态属性时指向实例，懒汉初始化时不赋值调用时先判断是否初始化过之后返回，优点启动快，线程安全(推荐)。
60. `public enum Season {SPRING,SUMMER,AUTUMN,WINTER}`,enum枚举类型，用来定义常量。常量一般全大写。
## 接口与继承
61. `interface`接口，通过关键字`implements`实现，必须提供接口中声明的方法,可以一次实现多个接口
    
    ```java
    implements AD,AP{  
        @Override
        public void magicAttack() {
            System.out.println("进行魔法攻击");
        }  
        @Override
        public void physicAttack() {
            System.out.println("进行物理攻击");
        }  
    }
    ```
    
62. `@Override` 表示重写方法

63. 子类转换为父类可直接转换，父类转子类必须进行强制转换，`ad = (ADHero) h;`

64. 转换失败会抛出异常 `ClassCastException 类型转换异常`

65. 类也可以转换成接口类型，同样向上转型一定可以，向下要强转

66. `System.out.println(h1 instanceof ADHero);`判断引用h1指向的对象，是否是ADHero类型

67. 子类可以继承父类的对象方法，同时，在继承后，可以重复提供该方法（覆盖，override）

68. 多态: 都是同一个类型，调用同一个方法，却能呈现不同的状态，分为操作符的多态`+`和类的多态

69. 多态使用方法：父类引用(接口)指向子类对象，同时调用的方法在子类中被重写。(接口和实现类也可以)

70. **隐藏**是子类覆盖父类的**类方法**，**重写是**子类覆盖父类的**对象方法**

71. 父类引用指向子类对象，调用时会使用父类的方法。因为类方法与对象无关，没有指向对象也可以调用。因此应当避免用对象引用调用类方法，应用类引用直接调用类方法

72. 使用关键字**super** 显式调用父类的构造方法，`super(XXX)`，调用父类属性，`super.XXX`

73. 实例化子类时默认调用父类无参构造方法

74. super可以用来在父类构造方法基础上重写子类构造方法

75. Object类是所有类的父类

76. Object类的一些方法，可以重写，`toString()`打印名称,`finalize()`回收对象,`equals()`判断指向是否相同,`hashCode`,`getClass`等。

77. final修饰一个类，则该类无法被继承；final修饰一个方法，则子类继承后该方法不能被重写；final修饰一个引用，则该引用只能指向一个对象之后不能变。

78. `public static final int itemTotalNumber = 6` 定义一个常量

79. String类为final类，不能被继承

80. 没有实现体的方法叫抽象方法，用`abstract`修饰，当一个类有抽象方法时，必须定义为抽象类

81. 抽象类不能被直接实例化，抽象类可以没有抽象方法

82. 抽象类被继承后必须提供对应的抽象方法

83. 抽象类和接口的区别：1）子类只能继承一个抽象类，可以实现多个接口；2）接口内定义的所有值都是`public static final`类型的常量，抽象类中可以提供任意属性的变量

84. 抽象类和接口中都可以定义实体方法，接口中需要用`default`修饰，称为默认方法

85. 在类中可以创建内部类，分为非静态内部类和静态内部类(用`static`修饰)，非静态需要先实例化外部类，静态不需要，实例化方法**new 外部类().new 内部类()** ，也可以拆开写

86. 通过内部类可以访问外部类private属性值

87. 在方法中可以创建本地类(也是内部类)，使用外部的局部变量时需要被修饰为final

88. 可以直接声明并实例化一个抽象类，直接使用他的抽象方法。这个类是一个新的类，没有命名称为匿名类

    ```java
    Hero h = new Hero(){
        public void attack() {
            System.out.println("新的进攻手段");
        }
    };
    h.attack();
    ```

89. 实现多个接口，同时默认方法重名时，必须在子类重写这个方法

90. super不能调用实现接口的默认方法

91. UML-Unified Module Language 统一建模语言

## 数字与字符串

92. 基本类型对应的类叫封装类

    ```java
    Integer it = new Integer(i);//把一个基本类型的变量,转换为Integer对象
    int i2 = it.intValue();//把一个Integer对象，转换为一个基本类型的int
    ```

93. 数字封装类有：`Byte,Short,Integer,Long,Float,Double`，是抽象类`Number`的子类，类首字母大写

94. **=符号**自动把 基本类型 转换为 类类型 就叫**装箱** ,反过来叫**拆箱**

    ```java
    int i = 5;
    Integer it2 = i; //自动转换就叫装箱
    int i3 = it2; //自动转换就叫拆箱
    ```

95. 调用类的最大最小值

    ```java
    System.out.println(Integer.MAX_VALUE); //int的最大值
    System.out.println(Integer.MIN_VALUE); //int的最小值 
    ```

96. 不同类型之间不能自动装箱拆箱，需要强制转换

97. 数字转字符串：

    1. String类的静态方法valueOf ：`String str = String.valueOf(i);`

    2. 先把基本类型装箱为对象，然后调用对象的toString：

       ```java
       Integer it = i;
       String str2 = it.toString();
       ```

98. 字符串转数字：调用Integer的静态方法parseInt：`int i= Integer.parseInt(str);`

99. 浮点数用法相同

100. java.lang.Math提供的一些静态方法：`Math.round(f1)`四舍五入，`Math.random()`[0,1)之间的随机浮点数，`(int)( Math.random()*10)`0-10之间的随机整数（取不到10）,`Math.sqrt(9)`，`Math.pow(2,4)`，`Math.PI`，`Math.E`

101. 格式化输出：%s 表示字符串，%d 表示数字，%n 表示换行，%8d总长度8,右对齐，%-8d总长度8,左对齐，%08d总长度8,补0，%,8d千位分隔符，%.2f小数后两位

     ```java
     String sentenceFormat ="%s 在进行了连续 %d 次击杀后，获得了 %s 的称号%n";
     System.out.printf(sentenceFormat,name,kill,title); //使用printf格式化输出
     System.out.format(sentenceFormat,name,kill,title); //使用format格式化输出,完全等同
     ```

102. char对应的封装类是Character，`Character c = c1; //自动装箱` 

103. Character常见方法：`Character.isLetter() `判断是否为字母,`.isDigit()`判断是否为数字,`.isWhitespace()`是否是空白,`.isUpperCase()`是否是大写,`.isLowerCase()`是否是小写,`.toUpperCase()`转大写,`.toLowerCase()`转小写,`.toString()`转字符串

104. 字符串转字符数组，`char[] cs = str.toCharArray();`

105.  创建字符串：1）每当有一个**字面值**出现的时候，虚拟机就会创建一个字符串，2）调用String的构造方法（传字面值或char数组），3）+号拼接

106. String类不能被继承(final)，String对象不能被改变(immutable,类似常量)

107. 字符串格式化：.format()  字符串长度：.length()

     ```java
     String sentenceFormat ="%s 在进行了连续 %d 次击杀后，获得了 %s 的称号%n";
     String sentence2 = String.format(sentenceFormat, name,kill,title);
     ```

108. .charAt(int index) 获取指定位置的字符,.toCharArray() 获取对应的字符数组

109. .substring(3) 截取从第3个开始的字符串(基0)  .substring(3,5) 左闭右开

110. `String subSentences[] = sentence.split(",");`根据,进行分割

111. .trim() 去掉首尾空格 .toLowerCase()转小写 .toUpperCase()转大写

112. .indexOf() 字符或字符串第一次出现的位置 .lastIndexOf() 最后一次出现位置

113. .indexOf(',',5)从位置5开始，出现的第一次,的位置  .contains() 是否包含子字符串

114. .replaceAll() 替换所有的 .replaceFirst() 只替换第一个

115. `System.out.println( str1 == str2);` ==用于判断是否是同一个字符串对象

116. **`.equals()`判断内容是否相同,不能用==**，`.equalsIgnoreCase()` 忽略大小写的比较

117. .startsWith() 判断是否以...开始  .endsWith() 判断是否以...结束（IgnoreCase忽略大小写）

118. StringBuffer可变长字符串：通过String初始化，.append()追加， .delete(``4``, ``10``)删除 ，.insert(``4``, "there")插入， .reverse() 反转

119. .length() 内容长度 .capacity() buffer容量

120. StringBuffer拼接性能比直接+好

 ## 日期、日历类

121. **java.util.Date;**日期类(注意不要混淆成 java.sql.Date)
122. `Date d1 = new Date();` 获取当前时间  .getTime()转long型整数
123. new Date().getTime() 和 System.currentTimeMillis() 是一样的
124. `SimpleDateFormat sdf =new SimpleDateFormat("yyyy/MM/dd HH:mm:ss" );`日期格式化
125. y 年 M 月 d 日 H 24进制小时 h 12进制小时 m 分 s 秒 S 毫秒
126. Date d = sdf.parse(str); 字符串转日期
127. java.util.Calendar;日历类
128. Calendar c = Calendar.getInstance();采用单例模式获取日历对象
129. Date d = c.getTime() 日历转日期 c.setTime(d) 日期转日历
130. `c.add(Calendar.MONTH, 1);`下个月的今天 `c.add(Calendar.YEAR, -1);`去年的今天 c.set(Calendar.DATE, ``3``); 这个月的第三天

