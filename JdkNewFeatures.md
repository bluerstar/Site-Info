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
--    AWT新增加了两个类:Desktop和SystemTray
    
######    使用JAXB2来实现对象与XML之间的映射
######    StAX
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
######    Annotation 注解
    
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
