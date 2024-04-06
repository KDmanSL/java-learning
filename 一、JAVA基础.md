**一、JAVA基础	**

1. JDK > JRE > JVM      JVM: JAVA 虚拟机      JRE：JAVA 运行环境（JVM + 核心类库）  JDK：JAVA开发工具包（JRE+开发工具）

2. JAVA 八种基本数据类型：byte 1, boolean T/F, char 2, short 2, int 4, float 4, long 8, double 8

   <img src="C:\Users\韶光善良君\AppData\Roaming\Typora\typora-user-images\image-20240309025553472.png" alt="image-20240309025553472" style="zoom:67%;" />
   java常见引用类型：String 集合 接口 类 

3. "=="与 equals() 方法的区别和联系：== 在基本数据类型：值比较, 引用类型时：地址比较
   equals 重写：值比较 ， equals不重写：地址比较

4. 字节码：.java文件通过 javac 编译可以变成.class文件也就是字节码（由两个十六进制值为一组，以字节为单位进行读取）

5. JAVA和C++的区别：C++有指针，支持多继承，JAVA允许一个类实现多个接口；JAVA完全面向对象，取消了C/C++中的结构和联合；JAVA自动进行无用内存回收；JAVA不支持操作符重载；JAVA有字符串变量；JAVA不支持goto的使用；JAVA不支持自动强制类型转换，需要显示进行强制类型转换。

6. switch(expr) case... expr可以是byte short char int String, long类型不可以

7. 访问控制符：public、private、protected、default
   ![image-20240309030154573](C:\Users\韶光善良君\AppData\Roaming\Typora\typora-user-images\image-20240309030154573.png)

8. break/continue/return 的区别和作用：
   break: 跳出总上一层循环，结束当前循环体
   continue: 结束本次循环，开始下一轮循环
   return: 结束当前方法，直接返回
   如何跳出多重嵌套循环：
   在外面定义一个标号，在里层循环时使用带有标号的break语句，如：break F;

9. final/finally/finalize 的区别：
   final: 修饰的变量为常量，修饰的方法无法被重写，修饰的类无法被继承
   finally: try/catch/finally，无论异常是否抛出，其中代码块都会运行，主要用于释放资源
   finalize: Object方法，目前JAVA已弃用

10. 效率计算2乘8 : 2<<3        相当于2*2^3

11. Math.round()方法四舍五入，具体操作是先加0.5然后向下取整。

12. float初始化需要这样：float f=3.4F

13. short s1=1;s1+=1; 隐含强制类型转换：s1=(short(s1+1));

14. static相关：静态资源，无法被override覆写，static方法不能引用非静态资源，非静态方法需要new过之后才可以使用。执行顺序：static静态代码块-->构造代码块-->构造函数-->普通代码块

15. & 与 &&：&为按位与 &&为逻辑与，&&存在短路特性，当前面一个条件无法为false时，后一个条件不会执行

16. 面向对象：易维护、易复用、易拓展、有封装、继承、多态的特性。
    面向过程：性能快，开销大，消耗资源。

17. 封装：把客观事物封装成抽象的类
    继承：使用现有类的所有功能，并在无需重写原来的类的情况下对这些功能进行拓展。
    多态：父类中定义的属性和方法子类继承后，可以具有不同的数据类型或表现出不同的行为。

18. 重载Overload和重写Override的区别是什么：
    重写发生在子类与父类之间，覆盖方法
    重载发生在一个类中，方法名相同，参数、返回值不同。

19. 构造函数只可以被重载但不可以被重写

20. 接口和抽象类的区别：

    1. 接口只有定义，不能有方法的实现，jdk1.8之后可以定义default方法体；抽象类可以有方法的实现
    2. 一个类可以实现多个接口，但只能继承一个抽象类。接口可以多重继承
    3. 接口强调功能的实现，抽象类强调所属关系
    4. 接口成员变量默认为public static final，抽象类成员变量默认为default。

21. java创建对象有哪几种方式：

    1. new创建新对象
    2. 通过反射机制 对象.newInstance()
    3. 采用clone机制
    4. 通过序列化机制

22. 深拷贝、浅拷贝：
    深拷贝：原对象和克隆对象不同，切对象内的成员引用也不同（实现Serializable接口，反序列化得到的对象的创建是深拷贝）
    浅拷贝：原对象和克隆对象不同，但对象内的成员引用相同（实现Cloneable接口的对象）

23. hashCode()与equals()的关系
    当进行值比较之前会先进行hashCode()比较计算hash值是否一致，若一致再进行equals()比较，判断值是否一致。hashCode相同，值不一定相同，如“重地”与“通话”。因此如果重写equals方法也要同时重写hashCode方法

24. String StringBuffer StringBuilder的区别
    String: 中使用一个final定义的char[]数组，故是不可变的，只能生成新的String对象，然后将地址指向新的String
    StringBuilder: 中使用的是char[]数组，是可变的，但是存在线程不安全问题
    StringBuffer在StringBuilder基础上对方法加了同步锁或者对调用的方法加了同步锁，所以是线程安全的。

25. String为何要设计成不可变的：1.保证安全：防止url之类的被更改，防止多线程安全问题。2.提高效率：实现字符串池，在堆中开辟一块存储空间String pool，当初始化一个String变量时，如果该字符串已经存在了，就不会去创建一个新的字符串变量，而是会返回已经存在了的字符串的引用。由于String是不可变的，保证了hashcode的唯一性，于是在创建对象时其hashcode就可以放心的缓存了，不需要重新计算。

26. 使用`String a = “aaa” ;`，程序运行时会在常量池中查找”aaa”字符串，若没有，会将”aaa”字符串放进常量池，再将其地址赋给a；若有，将找到的”aaa”字符串的地址赋给a。
    使用String b = new String("aaa");`，程序会在堆内存中开辟一片新空间存放新对象，同时会将”aaa”字符串放入常量池，相当于创建了两个对象，无论常量池中有没有”aaa”字符串，程序都会在堆内存中开辟一片新空间存放新对象。

27. 包装类型：推荐在POJO类中使用包装类型，因为从数据库查到的结果有可能为null，而基础数据类型不能为空。泛型中应该使用包装类型而非基础类型

28. Integer值比较：两个new 的Integer对象因为地址不同，所以判断是否“==”永远为false，但是当带有int类型比较时，会自动拆包成int进行值比较。两个非new生成的Integer对象，如果两个变量的值在区间-128到127之间，则比较结果为true，如果两个变量的值不在此区间，则比较结果为false。(因为当值在-128~127之间时，java会进行自动装箱，然后对值进行缓存，如果下次再有相同的值，会直接从缓存中取出使用。当值超出此范围，会在堆中new出一个对象来存储。)

29. 反射：获取一个类中的所有属性和方法。

    1. 获取类的Class对象实例 Class clz = Class.forName("com.zhenai.api.Apple");

    2. 根据Class对象实例获取Constructor对象Constructor appleConstructor = clz.getConstructor();

    3. 使用Constructor对象的newInstance方法获取反射类对象 Object appleObj = appleConstructor.newInstance();

    4. 获取方法的Method对象Method setPriceMethod = clz.getMethod("setPrice", int.class);

    5. 利用invoke方法调用方法 setPriceMethod.invoke(appleObj, 14);

       反射应用：JDBC，Spring xml配置模式

30. 泛型：将类型参数化，其在编译时才确定具体的参数。
    <? extends T>可以接受任何继承自T的类型（上届）只可读
    <? super T>可以接受任何T的父类（下界）只可写

31. Array不可以用泛型，编译器不允许创建泛型变量的数组，`ArrayList<String>`与`ArrayList<Integer>`是相等的，都是ArrayList.class

32. 序列化：把JAVA对象转换成字节序列，主要用于对象状态的保存与重建。实现Serializable接口或者Externalizable接口。序列化和反序列化通过比较serialVersionUID来验证版本一致性。

33. 异常：Error和Exception区别
    Exception：程序本身可以处理的异常，可以通过catch进行捕获处理。
    Error：程序本身无法处理的错误，无法通过catch捕获。

34. 非受检查异常就是不用进行异常处理的异常，例如NullPointException(空指针)`、`NumberFormatException（字符串转换为数字）等。
    受检查异常就是需要进行处理的异常，例如 IO 相关的异常、`ClassNotFoundException` 、`SQLException`等。

35. throw和throws：
    throw:用在方法内部，只能用于抛出一种异常，用来抛出方法或代码中的异常。
    throws:用在方法声明上，可以抛出多个异常，用来标识该方法可能抛出的异常列表。调用改方法的方法中必须包含处理异常的代码，否则也要在方法声明中用throws关键字抛出异常

36. NoClassDefFoundError 和 ClassNotFoundException区别：
    NoClassDefFoundError 是一个Error 类型的异常，是由JVM引起的，不应该尝试捕获该异常。
    ClassNotFoundException 是一个受检查异常，需要显示地使用try-catch对其进行捕获和处理，或在方法声明用throws抛出异常。

37. try-catch-finally 中 catch是可以省略的，try可以处理运行时异常，try+catch适合处理运行时异常+普通异常。即便在catch中return了，finally还会执行。

38. IO流：字节流：适合所有类型文件的数据传输。字符流：只能处理文本信息，处理文本要比字节流方便。

39. BIO NIO AIO：
    BIO：同步阻塞式，一个连接一个线程，一旦接受客户端连接，就无能接受其他客户端连接请求。可以通过多线程来支持多个客户端的连接，但是会导致服务器CPU高消耗。
    NIO：同步非阻塞式，一个请求一个线程，请求会注册到多路复用器Selector上，当多路复用器轮询到连接有IO请求才启动一个线程处理。但是维护成本高，容易出Bug。
    AIO：异步非阻塞式，NIO加强版，一个有效请求一个线程，客户端IO都是由操作系统先完成后，再通知服务器应用去启动线程进行处理。

40. JAVA IO使用的到的设计模式：
    适配器模式：中间类帮助两个接口不匹配的类在一起工作。InputStreamReader ：字节流-->字符流
    装饰器模式：一种动态网一个类中添加新的行为的设计模式，比生成子类更加灵活，可以给对象添加一些功能。new BufferedInputStream(new FileInputStream(inputStream));

41. 进程、线程、多进程、多线程：
    进程：是操作系统资源分配的基本单位，运行一个程序就是运行一个进程。
    线程：是处理器任务调度和执行的基本单位，一个进程可以开多个线程。
    多进程：多个进程同时运行调度（同时开多个程序），当一个进程崩溃时，其他进程任然能够继续运行。
    多线程：一个进程同时调度多个线程，当一个线程崩溃时，整个进程都会死掉。

42. 创建线程的三种方式：

    1. 继承Thread类：1.创建一个继承于Thread类的子类。 2.重写run()方法。3.创建Thread类的子类的对象。4.通过start()执行进程。劣势：线程类无法继承其他父类
    2. 实现Runnable接口：1.创建一个实现了Runnable接口的类。2.重写run()方法。3.创建实现类对象。4.将此对象作为参数传递到Thread类的构造器中，创建Thread类的对象。5.通过Thread类的对象调用start()。
    3. 实现Callable接口：1.创建一个实现了Callable接口的类。2.重写call()方法。3.创建实现类对象。4.将此对象作为参数传递到FutureTask构造器中，创建FutureTask的对象。5.将FutureTask对象作为参数传递到Thread类的构造器中，创建Thread对象，调用start()。6.获取Callable中call方法的返回值。<img src="C:\Users\韶光善良君\AppData\Roaming\Typora\typora-user-images\image-20240316174318563.png" alt="image-20240316174318563" style="zoom:50%;" />

43. 线程的生命周期：<img src="https://camo.githubusercontent.com/10f1a765d1a1d72dfc87244e868b474c60ee34866539a9ab2e450ee0300391d7/68747470733a2f2f796f757a68697875657975616e2e636f6d2f626c6f672f77702d636f6e74656e742f75706c6f6164732f323031392f30382f32303139303830313231323334315f37303537342e6a7067" alt="img" style="zoom:50%;" />

44. 线程死锁：A有a要b，B有b要a。<img src="https://camo.githubusercontent.com/ed6b7dae553c1ccacd2ebb6475018b165b917214299322fb18a6737f1317b3b4/687474703a2f2f626c6f672d696d672e636f6f6c73656e2e636e2f696d672f313538333332373032323336355f31332e706e67" alt="img" style="zoom:33%;" />
    死锁条件：

    1. 互斥条件，该资源同一时刻只能被一个线程占用。
    2. 请求与保持条件：一个线程因请求资源而阻塞时，已有资源保持不释放。
    3. 不剥夺条件：线程已获得的资源在未使用完之前不能被其他线程强行剥夺。
    4. 循环等待条件：若干线程之间形成一种头尾相接的循环等待资源关系。

    避免死锁：破坏条件之一

    1. 破坏互斥条件：无法破坏（用锁就是为了让资源使用互斥的）
    2. 破坏请求与保持条件：破坏请求：必须先成功申请到全部资源后再执行。破坏保持：每个进程提出申请资源前必须释放已占有的一切资源。
    3. 破坏不剥夺条件：1.走不通就释放全部资源，进入等待状态。2.走不通就去抢别人的，抢不到就放弃自己的。(检查已获得资源的进程状态，如果状态为等待资源状态，则抢占该资源，否则自己进入等待资源状态)
    4. 破坏循环等待条件：给所有资源类型进行排序编号，每个进程只能按照递增的顺序来申请资源，如果需要同一个资源类型的多个资源则需要一起申请，如果进程后面需要申请序号低的资源，就需要把现在有的改序号资源以上的资源全部释放。

45. shutdown():关闭线程池，停止接受新任务，原本的任务继续执行。
    shutdownNow():关闭线程池，停止接受新任务，原来的任务停止运行。

46. sleep():是Thread类的静态方法，当前线程将睡眠n毫秒，线程进入阻塞状态。睡眠时间到了后解除阻塞，进入运行状态。睡眠不释放锁。
    wait():是Object的方法，必须与synchronized关键字一起用，线程进入阻塞状态，当notify或者notifyall被调用后，会解除阻塞。睡眠时释放锁。
    sleep主要用于暂停执行，wait主要用于线程通信。

47. 为什么要调用start()而不直接执行run()方法：start()会启动一个线程，并使线程进入就绪状态，当分配到时间片后就自动执行run()方法的内容。直接执行run方法，会把run当成main线程下的普通方法去执行，并不会在某个线程中执行它。

48. Thread类中的yield方法可以暂停当前正在执行的线程对象，让其他有相同优先级的线程执行。

49. volatile保证变量对所有线程的可见性，当volatile变量被修改，新值对所有线程会立即更新。

50. Spring  IOC: 控制反转，由原本的对象自己创建实例对象，改为由IOC容器创建对象，从而避免重复创建对象，达到松耦合的特点。
                DI：依赖注入，将对象依赖的对象传递进去，构造器注入，setter注入，接口注入，注解注入。

51. Spring 中的bean的作用域：

    1. singleton: 唯一bean实例，所有请求都是对应同一个bean实例
    2. prototype: 每次请求都会创建一个新的bean实例
    3. request: 每次HTTP请求都会产生一个新的bean
    4. session: 同一个session中共享 一个bean，不同session使用不同的bean
    5. global-session: 一般用于portlet应用环境。

52. bean的注解：
    @Component: 通用的注解，可标注任意类为spring的组件。
    @Service: 服务层
    @Repository: 持久层 dao
    @Controller: 控制层

53. AOP，面向切面编程，可以拦截指定方法并且对方法增强，而且无需侵入业务代码中。主要用于日志记录、事务管理、权限验证、性能监测。

54. Spring设计模式：
    **工厂设计模式** : Spring使用工厂模式通过 `BeanFactory`、`ApplicationContext` 创建 bean 对象。

    **代理设计模式** : Spring AOP 功能的实现。

    **单例设计模式** : Spring 中的 Bean 默认都是单例的。

    **模板方法模式** : Spring 中 `jdbcTemplate`、`hibernateTemplate` 等以 Template 结尾的对数据库操作的类，它们就使用到了模板模式。

    **包装器设计模式** : 我们的项目需要连接多个数据库，而且不同的客户在每次访问中根据需要会去访问不同的数据库。这种模式让我们可以根据客户的需求能够动态切换不同的数据源。

    **观察者模式:** Spring 事件驱动模型就是观察者模式很经典的一个应用。

    **适配器模式** :Spring AOP 的增强或通知(Advice)使用到了适配器模式、spring MVC 中也是用到了适配器模式适配`Controller`。

55. @RestController 和 @Controller ：@RestController 在 @Controller 基础上，增加了 @ResponseBody 注解，更加适合目前前后端分离的架构下，提供Restful API ,返回例如JSON数据格式。

56. @RequestMapping 和 @GetMapping 注解的不同之处：@RequestMapping 可注解在类和方法上；@GetMapping 仅可注册在方法上。@RequestMapping 可进行GET, POST, PUT, DELETE 等请求；@GetMapping 是@RequestMapping的GET方法的特例。

57. @PathVariable 和@RequestParam的区别：都可以用于方法参数，两者输入的部分不同，PathVariable输入的是url，RequestParam输入的是参数部分，当业务指向某一个具体的资源时，使用PathVariable，例如/blogs/{blogId}，当业务主要用来对资源进行过滤筛选时，使用RequestParam，例如/blogs?state=publish

58. REST软件架构：URL中只使用名词来定位资源，用HTTP协议里的动词（GET、POST、PUT、DELETE）来实现资源的增删改查操作。
    增加一个朋友，uri: generalcode.cn/va/friends 接口类型：POST
    删除一个朋友，uri: generalcode.cn/va/friends 接口类型：DELETE（在http的parameter指定好友id）
    修改一个朋友，uri: generalcode.cn/va/friends 接口类型：PUT（在http的parameter指定好友id）
    查找一个朋友，uri: generalcode.cn/va/friends 接口类型：GET
    安全性：一些 HTTP 操作是安全的，如 GET 和 HEAD ，它不能在服务端修改资源，换句话说，PUT、POST 和 DELETE 是不安全的，因为他们能修改服务端的资源。
    所以，是否安全的界限，在于**是否修改**服务端的资源

59. Spring boot中的核心注解：@SpringBootApplication启动类{包含@SpringBootConfiguration(配置文件)，@EnableAutoConfiguration(开启自动装配)，@ComponentScan(Spring组件扫描)

//45.
