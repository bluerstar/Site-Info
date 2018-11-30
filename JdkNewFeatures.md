### 1. JDK5:
######    泛型(Generics)
    List<String> userNames = new ArrayList<String>();
    String userName = userNames.get(0);
    类型统配符？代替具体的实参。List<?> 是List<String>和List<Integer>的父类
    类型通配符上限通过形如Box<? extends Number>形式定义，类型通配符下限为Box<? super Number>形式
    Java中没有所谓的泛型数组一说
    ps:http://www.cnblogs.com/lwbqqyumidi/p/3837629.html
    
######    增强for循环
    引入增强for循环的原因：替代Iterator
    for/in语句的适用范围：
        遍历数组
        遍历实现Iterable接口的集合类
    增强for循环底层实现也是迭代器，可以通过class文件查看

######    可变参数   
    如果说实现的多个方法，这些方法中逻辑基本相同，唯一不同的是传递参数的个数，那么可以使用可变参数。
    注意：
        （1）可变参数只能写在方法的参数列表中，不能单独定义。
        （2）在方法的参数列表中只能有一个可变参数。
        （3）如果有其他参数，则可变参数必须放在参数列表的最后。
    
######    自动拆装箱（Autoboxing/unboxing）
    装箱：
        把基本的数据类型转换成包装类。
    拆箱：
        把包装类转换成基本的数据类型。
    自动装箱：
        Integer i = 10;
    自动拆箱：
        int j = i;

######    类型安全的枚举（Typesafeenums）
    枚举类案例：
        有参构造方法枚举类型
            需要在每个实例上都写上参数：Week(String s) {}   →   Sunday("")
        带有抽象方法的枚举类型举例
            在枚举的每个实例中都要重写这个抽象方法。
            
    枚举API
            String name(): 返回枚举的名称。
            int ordinal(): 返回枚举的下标，下标从0开始。
            static Enum valueOf(Class enumType, String name): 返回枚举的对象。 

        自定义的枚举类，在编译阶段自动生成两个方法：
        Enum valueof(String name): 获取枚举对象。
        Enum[] values(): 获得所有枚举对象的数组。    
            
######    静态导入（static import）
    可以在代码中，直接使用静态导入方式，导入静态方法或者常量
    静态导入的格式import static 报名.类名.静态成员，静态导入可以作用一个类的所有静态成员
    注意：当在自定义的类中也出现了静态同名的方法，会优先调用本地方法
    
######    元数据（metadata）

######    线程池
    
### 2. JDK6:
######    Desktop类和SystemTray类
    AWT新增加了两个类:Desktop和SystemTray
    前者可以用来打开系统默认浏览器浏览指定的URL,打开系统默认邮件客户端给指定的邮箱发邮件,用默认应用程序打开或编辑文件(比如,用记事本打开以txt为后缀名的文件),用系统默认的打印机打印文档;后者可以用来在系统托盘区创建一个托盘程序. 
    
######    使用JAXB2来实现对象与XML之间的映射
    JAXB是Java Architecture for XML Binding的缩写，可以将一个Java对象转变成为XML格式，反之亦然。 
    我们把对象与关系数据库之间的映射称为ORM, 其实也可以把对象与XML之间的映射称为OXM(Object XML Mapping). 原来JAXB是Java EE的一部分，在JDK6中，SUN将其放到了Java SE中，这也是SUN的一贯做法。JDK6中自带的这个JAXB版本是2.0, 比起1.0(JSR 31)来，JAXB2(JSR 222)用JDK5的新特性Annotation来标识要作绑定的类和属性等，这就极大简化了开发的工作量。 
    实际上，在Java EE 5.0中，EJB和Web Services也通过Annotation来简化开发工作。另外,JAXB2在底层是用StAX(JSR 173)来处理XML文档。除了JAXB之外，我们还可以通过XMLBeans和Castor等来实现同样的功能。
    
######    StAX
    StAX(JSR 173)是JDK6.0中除了DOM和SAX之外的又一种处理XML文档的API。 
    StAX的来历 ：在JAXP1.3(JSR 206)有两种处理XML文档的方法:DOM(Document Object Model)和SAX(Simple API for XML). 
    由于JDK6.0中的JAXB2(JSR 222)和JAX-WS 2.0(JSR 224)都会用到StAX所以Sun决定把StAX加入到JAXP家族当中来，并将JAXP的版本升级到1.4(JAXP1.4是JAXP1.3的维护版 本). JDK6里面JAXP的版本就是1.4. 。 
    StAX是The Streaming API for XML的缩写，一种利用拉模式解析(pull-parsing)XML文档的API.StAX通过提供一种基于事件迭代器(Iterator)的API让 程序员去控制xml文档解析过程,程序遍历这个事件迭代器去处理每一个解析事件，解析事件可以看做是程序拉出来的，也就是程序促使解析器产生一个解析事件 然后处理该事件，之后又促使解析器产生下一个解析事件，如此循环直到碰到文档结束符； 
    SAX也是基于事件处理xml文档，但却 是用推模式解析，解析器解析完整个xml文档后，才产生解析事件，然后推给程序去处理这些事件；DOM 采用的方式是将整个xml文档映射到一颗内存树，这样就可以很容易地得到父节点和子结点以及兄弟节点的数据，但如果文档很大，将会严重影响性能。
    
######    使用Compiler API
######    轻量级Http Server API
######    插入式注解处理API(Pluggable Annotation Processing API)
######    用Console开发控制台程序
######    对脚本语言的支持
######    Common Annotations
    
### 3. JDK7:
######    对集合类的语言支持 
######    自动资源管理 
######    增强的对通用实例创建（diamond）的类型推断 
######    数字字面量下划线支持 
######    switch中使用string 
######    二进制字面量 
######    简化的可变参数调用 
    
### 4. JDK8:
######    接口的默认方法
######    Lambda 表达式
######    函数式接口
######    方法与构造函数引用
######    Lambda 作用域
######    访问局部变量
######    访问对象字段与静态变量
######    访问接口的默认方法
######    Date API
######    Annotation注解
    
### 5. JDK9:
######    Java 平台级模块系统
######    Linking
######    JShell: 交互式 Java REPL
######    改进的 Javadoc
######    集合工厂方法
######    改进的 Stream API
######    私有接口方法
######    HTTP/2
######    多版本兼容 JAR
    
 ### 6. JDK10:
######    局部变量类型推断
    JDK10 可以使用var作为局部变量类型推断标识符，此符号仅适用于局部变量，增强for循环的索引，以及传统for循环的本地变量；它不能使用于方法形式参数，构造函数形式参数，方法返回类型，字段，catch形式参数或任何其他类型的变量声明。
    标识符var不是关键字；相反，它是一个保留的类型名称。这意味着var用作变量，方法名或则包名称的代码不会受到影响；但var不能作为类或则接口的名字（但这样命名是比较罕见的，因为他违反了通常的命名约定，类和接口首字母应该大写）
    参考示例：
    var str = "ABC"; //根据推断为 字符串类型
    var l = 10L;//根据10L 推断long 类型
    var flag = true;//根据 true推断 boolean 类型
    var flag1 = 1;//这里会推断boolean类型。0表示false 非0表示true
    var list = new ArrayList<String>();  // 推断 ArrayList<String>
    var stream = list.stream();          // 推断 Stream<String>
    
    被编译class文件：
    String str = "ABC";
    long l = 10L;
    boolean flag = true;
    int flag1 = true;
    ArrayList<String> list = new ArrayList();
    Stream<String> stream = list.stream();

######    将JDK多存储库合并为单储存库
######    垃圾回收接口
######    并行Full GC 的G1
######    应用数据共享
######    线程局部管控
######    移除Native-Header Generation Tool （javah）
######    Unicode 标签扩展
######    备用内存设备上分配堆内存
######    基于实验JAVA 的JIT 编译器
######    Root 证书
######    基于时间的版本控制
