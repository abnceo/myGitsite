# 《Swift5从零到精通iOS开发训练营》

### 第1部分 Swift语言基础语法
    
#### 第2章 数据类型：

    ```swift
    var a5 = MemoryLayout<UInt>.size // 获取数据类型所占位数，在64位机器上UInt占8字节64位
    var sum = 1.25e3 // 1.25*(10^3)=1250，e表示10的n次方
    var sum2 = 0x1p3 // 1*(2^3)=8, p表示2的n次方
    // swift语言无论是整型数据还是浮点数据，都可以在数字前加任意个0来进行位数填充，也可以在数字中加入下划线进行分隔。
    var num1 = 001.23  //1.23
    var num2 = 1_000   //1000
    var num3 = 1_000.1_001  // 1000.1001

    // Swift语言还支持种特殊的基本数据类型，分别是元组类型和可选值类型。
    var pen:(name:String, price:Int) = ("钢笔"，2)
    var name = pen.name // 获取pen变量名称
    var name0 = pen.0  // 元组会自动位每个参数分配下标，下标值从0开始依次递增
    var price = pen.price  // 获取pen变量价格
    var (theName,thePrice) = pen   // 元组实例被创建后，开发者也可以通过指定的变量或者常量来分解它。或称之为拆包或解包
    // swift语言中，常常使用符号"_"来表示匿名的概念，因此"_"也被称为匿名标识符。
    // 元组虽然使用起来十分方便，但是其知识用于简单数据的组合，对于结构复杂的数据，要采用结构体或者类来实现。

    // swift语言中，如果使用了一个没有赋值的变量，程序就会报错并停止运行。-- 可选值类型的由来
    var obj:String?
    if obj == nil {}
    //Optional类型不会独立存在，总是附着于某个具体的数据类型之上。具体类型可以是基本数据类型，也可以是结构体或类等。
    //?也可以出现在实例后面，则代表的是可选链的调用（后续介绍）
 

    // 当我们需要访问可选类型的值时，必须先进行解包操作。 解包是将可选类型转换为非可选类型的过程。 Swift提供了多种解包方式，包括强制解包、可选绑定和隐式解包等。 强制解包使用感叹号（!）来访问可选类型的值。 如果可选类型包含值，强制解包会返回该值；如果可选类型为nil，则会触发运行时错误。 因此，在使用强制解包时，我们必须确保可选类型一定包含值，以避免程序崩溃

    //!出现在实例后面，代表的是对Optional类型实例的拆包操作 - forced unwrapping （强制解包）
    // 隐式解包 （Implicitly Unwrapped Optionals）是一种特殊的可选类型，它在声明时带有感叹号（!），但在使用时不需要显式解包。隐式解包的变量在首次赋值后，可以被当作非可选类型来使用。如果隐式解包的变量在访问时为nil，同样会触发运行时错误。隐式解包适用于那些在初始化时就被赋值，并且在后续代码中不会被设置为nil的变量 
    var implicitlyUnwrappedNumber: Int! = 10
    let sum = implicitlyUnwrappedNumber + 5 // 隐式解包，假设implicitlyUnwrappedNumber不为nil

    // if-let 用于多个optional类型值的绑定时，只有所有optional值都不为nil，绑定才会成功，代码执行才会进入到if为真的代码块中。这个方式常被称为 optional binding (可选绑定)

    var obj:String? = "HS"
    if let tmp = obj { // if-let 绑定，在实际应用中十分广泛， 创建了临时常量tmp来接收obj拆包后的值。
        print(tmp)
    }else{
        obj = "HS"
        print(obj!)
    }

    //swift语言使用typealias关键字来实现别名：
    typealias Price = Int // 为Int类型取一个别名Price
    var penPrice:Price = 100
    ```

#### 第3章 字符/字符串与集合类型
    ```swift
    str = String(describe: (1,1.0,true)) // 通过元组构造“（1，1.0，true）
    str = String(format:"我是%@", "周杰伦")  // 通过格式化字符串构造“我是周杰伦“
    var c2 = "world"
    var d2 = "Hello \(c2)"  // "Hello world"

    ```

    
- 第2部分 iOS开发基础
- 第3部分 实战


