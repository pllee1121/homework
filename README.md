## 观察者模式的使用的范围：
  * 一个抽象模型有两个方面：
    其中一个方面依赖另一个方面，将这两个方面的封装在独立的对象中是使他们可以各自独立地改变和复用
  * 一个对象的改变将导致一个或者多个其他对象发生改变，而**并不知道有多少对象将发生改变，也不知道这些对象是谁**
  * 需要在系统中创建一个触发链，A对象的行为将影响B对象，B对象的行为将影响C对象...... 可以使用观察者模式创建一种链式触发机制

## 观察者模式的优缺点:
  * 优点
    * **可以实现表示层和数据逻辑层的分离** ，定义了稳定的消息更新传递机制，并抽象了更新接口，使得可以有各种各样不同的表示层充当具体观察者角色
    * 在观察目标和观察者之间**建立一个抽象的耦合**，观察目标只需要维持一个抽象观察者的集合，无须了解其具体观察者，由于观察目标和观察者没有紧密地耦合在一起，因此它们可以属于不同的抽象化层次
    * **支持广播通信** ，观察目标会向所有已注册的观察者对象发送通知，**简化了一对多系统设计的难度**
    * **符合开闭原则** ，增加新的具体观察者无须修改原有系统代码，在具体观察这与观察目标之间不存在关联关系的情况下增加新的观察目标也很方便

  * 缺点
    * 如果一个观察目标对象有很多直接和间接观察者，将所有的观察者都通知会花很多时间
    * 如果在观察者和观察目标之间存在循环依赖，观察目标会触发它们之间进行循环调用，可能会导致系统奔溃
    * 观察者模式没有相应的机制让观察者知道所观察的目标对象是怎么发生变坏的而仅仅只是知道观察者目标发生了变化

## MVC
  * MVC是模型( Model )，视图( View )和控制( Control )的缩写，其目的是实现Web系统的职能分工。其中，模型层实现系统中的业务逻辑；视图层用于与用户交互；控制层是模型与视图之间沟通的桥梁，可以分派用户的请求



  * 控制器
    * 接收用户输入，并完成模型，视图的调用。Control处理用户交互，从Model中获取数据并将数据传给指定的View
    * View是用户接口层组件，主要是将Model中的数据展示给用户
    * Model 主要是存储或者是处理数据的组件，实现业务逻辑层对实体类相应数据库的操作，如CRUD（Create、Read、Update、Delete），包括数据、验证规则、数据访问和业务逻辑等应用程序信息

## 常用模式
  * 工厂方法模式
  * 抽象工厂模式
  * 外观模式
  * 迭代器模式
  * 观察者模式

## 第二梯队模式
  * 单例模式
  * 适配器模式
  * 组合模式
  * 代理模式
  * 命令模式
  * 策略模式

## 单例模式
  * 如何保证一个类只有一个实例，并且这个实例易于被访问？定义一个统一的全局变量可以确保对象随时可以被访问，但是**不能防止创建多个对象**( 解决技术让类自身负责和保存它的唯一实例，并保证不能创建其他实例，它还提供一个访问该实例的一个方法)

  * 官方定义: 确保**一个类只有一个实例**，并且提供一个**全局访问点**来访问这个**唯一实例**

  * 单例模式三个要点：
    * 某个类只能有一个实例
    * 必须自行创建这个实例
    * 必须自行向整个系统提供这个实例


  * 单例模式的代码实现原理
    * 单例模式的目的是**保证一个类有且只有一个实例**，并提供一个访问它**全局的访问点**
    * 单例模式**包含的角色只有一个**，也就是单例类Singleton
    * 单例类**拥有一个私有的的构造函数，确保用户无法通过new关键字直接实例化**
    * 在单例模式中，还包括一个静态私有**成员变量和静态共有的工厂方法，该工厂方法负责检验实例的存在性并实例话自己**，然后存储在静态成员变量中，以确保只有一个实例被创建


  * 代码实现过程需要注意的事项
    * 实例类构造函数的可见性为private
    * 提供一个类型为自身的静态私有成员变量
    * 提供一个共有的静态方法
  * 单例模式的使用环境
    * 1.系统只需要一个实例对象
    * 2.由于在系统内存中，只存在一个对象，因此可以节约系统资源，对于一个需要频繁创建和删除的的对象

## 单例模式的优缺点
  * 优点
     * 单例模式提供了对唯一实例的受控访问，因为单例模式封装了他的唯一实例，所以它可以严格控制客户怎样以及何时访问它
     * 由于在系统内存中只存在一个对象，因此可以节约系统资源，对于一些需要繁琐创建和销毁的对象，单例模式无疑可以提高系统性能
     * 允许可变数据的实例。基于单例模式可以进行扩展，使得与控制单例模式相似的方法来获得指定个数的实例对象，既节约系统资源，又解决了由于单例对象共享过多有损性能的问题。
  * 缺点
     * 由于单例模式中没有抽象层，因此单例类的扩展有很大的困难
     * 单例类的职责过重，在一定程度上违背了**单一职责**原则。因为单例类提供了业务方法，又提供了创建对象的方法（工厂方法），将对象的创建和对象本身的功能耦合在一起
     * 现在有很多面向对象的运行环境,提供了自行垃圾回收技术，因此如果实例化的共享对象长时间不被利用，系统会认为它是垃圾，会自动销毁并回收资源，下次利用又重新实例化，这将导致共享的单例对象状态的丢失
