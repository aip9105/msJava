

# Java基础知识—上篇

## 1. 面向对象-OOP特性

> 面向对象编程思想把所有的有形或无形的事物都看作对象，并给对象赋予相应的属性和行为，建立对象之间的联系，使程序员更加立体、形象地解决编程领域的问题。——摘自《码出高效Java开发手册》

### 抽象

**抽象**是面向对象思想最基础的能力之一，正确而严谨的业务抽象和建模分析能力是后续的封装、继承、多态的基础，是软件大厦的基石。

### 封装

**封装**是对象功能内聚的表现形式，在抽象基础上决定信息是否公开及公开等级，核心问题是以什么方式暴漏哪些信息。主要任务是对属性、数据、敏感行为实现隐藏，对属性的访问和修改必须通过公共接口实现。封装使对象关系变得简单，降低了代码耦合度，方便维护。

### 继承

**继承**用来扩展一个类，子类可继承父类的部分属性和行为使模块具有复用性。继承是"is-a"关系，可使用里氏替换原则判断是否满足"is-a"关系，即任何父类出现的地方子类都可以出现。如果父类引用直接使用子类引用来代替且可以正确编译并执行，输出结果符合子类场景预期，那么说明两个类符合里氏替换原则。

### 多态

**多态**以封装和继承为基础，根据运行时对象实际类型使同一行为具有不同表现形式。多态指在编译层面无法确定最终调用的方法体，在运行期由 JVM 动态绑定，调用合适的重写方法。由于重载属于静态绑定，本质上重载结果是完全不同的方法，因此多态一般专指重写。

## 2. 重载和重写

**重载**指方法名称相同，但参数类型个数不同，是行为水平方向不同实现。对编译器来说，方法名称和参数列表组成了一个唯一键，称为方法签名，JVM 通过方法签名决定调用哪种重载方法。不管继承关系如何复杂，重载在编译时可以根据规则知道调用哪种目标方法，因此属于静态绑定。

JVM 在重载方法中选择合适方法的顺序：① 精确匹配。② 基本数据类型自动转换成更大表示范围。③ 自动拆箱与装箱。④ 子类向上转型。⑤ 可变参数。

**重写**指子类实现接口或继承父类时，保持方法签名完全相同，实现不同方法体，是行为垂直方向不同实现。

元空间有一个方法表保存方法信息，如果子类重写了父类的方法，则方法表中的方法引用会指向子类实现。父类引用执行子类方法时无法调用子类存在而父类不存在的方法。

重写方法访问权限不能变小，返回类型和抛出的异常类型不能变大，必须加 `@Override` 。

## 3. 接口和抽象类

接口和抽象类对实体类进行更高层次的抽象，仅定义公共行为和特征。抽象类的存在只是为了降低面向接口编程的难度。

| 语法维度 |                       抽象类                       |                             接口                             |
| :------: | :------------------------------------------------: | :----------------------------------------------------------: |
| 成员变量 |                     无特殊要求                     |                默认 public static final 常量                 |
| 构造方法 |               有构造方法，不能实例化               |                   没有构造方法，不能实例化                   |
|   方法   | 抽象类可以没有抽象方法，但有抽象方法一定是抽象类。 | 默认 public abstract，JDK8 支持默认/静态方法，JDK9 支持私有方法。 |
|   继承   |                       单继承                       |                            多继承                            |

当纠结定义接口和抽象类时，推荐定义为接口，遵循接口隔离原则，按维度划分成多个接口，再利用抽象类去实现这些，方便后续的扩展和重构。

## 4. 访问权限控制

| 访问权限控制符 | 任何地方 | 包外子类 | 包内 | 类内 |
| :------------: | :------: | :------: | :--: | :--: |
|     public     |    √     |    √     |  √   |  √   |
|   protected    |    ×     |    √     |  √   |  √   |
|       无       |    ×     |    ×     |  √   |  √   |
|    private     |    ×     |    ×     |  ×   |  √   |

- `public`  ：可以修饰外部类、属性、方法，表示公开的、无限制的。被public所修饰的类、属性和方法不仅可以被包内访问，还可以跨类、跨包访问，甚至允许跨工程访问。
- `protected`  ：只能修饰属性和方法，表示受保护的、有限制的。被protected所修饰的属性和方法能被包内及包外子类访问。
- `无` ：即没有任何访问权限控制符，表示仅对包内可见。
- `private `   :  只能修饰属性、方法和内部类。表示私有的。被private所修饰的属性或方法只能在该类内部访问。

## 5. 

