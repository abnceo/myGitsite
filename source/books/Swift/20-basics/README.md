# 快速入门

### [官网的tour guide](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/guidedtour/) - 用于检查你是否掌握这部分的内容

语法基础主要包含如下几个部分：
1. 

- 允许开发者省略分号，自动以换行来分隔语句。同时支持一行中编写多句代码，此时要使用分号分隔
- var a:Int = 1, b:Float = 2.0, c:Bool = true, d:Sting = "hello"
- 常量和变量的定义：
  - 使用 let 定义常量，使用 var 定义变量
  - 常量和变量的命名规则:不能以数字开头
- Create **arrays and dictionaries** using brackets ([]), and access their elements by writing the index or key in brackets. A comma is allowed after the last element.
  ```swift
  var fruits = ["strawberries", "limes", "tangerines"]
  fruits[1] = "grapes"

  var occupations = [
      "Malcolm": "Captain",
      "Kaylee": "Mechanic",
  ]
  occupations["Jayne"] = "Public Relations"
  ``` 
- If you’re assigning an **empty array or dictionary to a new variable**, or another place where there isn’t any type information, you need to specify the type.
```swift
let emptyArray: [String] = []
let emptyDictionary: [String: Float] = [:]
```
- Use if and switch to make conditionals, and use for-in, while, and repeat-while to make loops. **Parentheses around the condition or loop variable are optional. Braces around the body are required.**
- You can write if or switch after the equal sign (=) of an assignment or after return, to choose a value based on the condition.
```swift
let scoreDecoration = if teamScore > 10 {
    "🎉"
} else {
    ""
}
print("Score:", teamScore, scoreDecoration)
// Prints "Score: 11 🎉"
```
- You can use **if and let** together to work with values that might be missing. These values are represented as optionals. An optional value either contains a value or contains nil to indicate that a value is missing. **Write a question mark (?) after the type of a value to mark the value as optional.**
```swift
var optionalString: String? = "Hello"
print(optionalString == nil)
// Prints "false"

var optionalName: String? = "John Appleseed"
var greeting = "Hello!"
if let name = optionalName {
    greeting = "Hello, \(name)"
}
```
- Another way to handle optional values is to **provide a default value using the ?? operator.** If the optional value is missing, the default value is used instead.
```swift
let nickname: String? = nil
let fullName: String = "John Appleseed"
let informalGreeting = "Hi \(nickname ?? fullName)"
```
- Switches support any kind of data and a wide variety of comparison operations — they aren’t limited to integers and tests for equality.
```swift
let vegetable = "red pepper"
switch vegetable {
case "celery":
    print("Add some raisins and make ants on a log.")
case "cucumber", "watercress":
    print("That would make a good tea sandwich.")
case let x where x.hasSuffix("pepper"):
    print("Is it a spicy \(x)?")
default:
    print("Everything tastes good in soup.")
}
// Prints "Is it a spicy red pepper?"
```
- You can keep an index in a loop by using ..< to make a range of indexes. Use **..< to make a range that omits its upper value, and use ... to make a range that includes both values.**
```swift
var total = 0
for i in 0..<4 {
    total += i
}
print(total)
// Prints "6"
```
- Use func to declare a function. Call a function by following its name with a list of arguments in parentheses. **Use -> to separate the parameter names and types from the function’s return type.**
```swift
func greet(person: String, day: String) -> String {
    return "Hello \(person), today is \(day)."
}
greet(person: "Bob", day: "Tuesday")
```
- By default, functions use their parameter names as labels for their arguments. Write a **custom argument label** before the parameter name, or write **_ to use no argument label.**
```swift
func greet(_ person: String, on day: String) -> String {
    return "Hello \(person), today is \(day)."
}
greet("John", on: "Wednesday")
```
- Use a tuple to make a compound value — for example, to **return multiple values from a function.** The elements of a tuple can be referred to either by name or by number.
```swift
func calculateStatistics(scores: [Int]) -> (min: Int, max: Int, sum: Int) {
    var min = scores[0]
    var max = scores[0]
    var sum = 0


    for score in scores {
        if score > max {
            max = score
        } else if score < min {
            min = score
        }
        sum += score
    }


    return (min, max, sum)
}
let statistics = calculateStatistics(scores: [5, 3, 100, 3, 9])
print(statistics.sum)
// Prints "120"
print(statistics.2)
// Prints "120"
```
- Functions are a first-class type. This means that a function can **return another function** as its value.
```swift
func makeIncrementer() -> ((Int) -> Int) {
    func addOne(number: Int) -> Int {
        return 1 + number
    }
    return addOne
}
var increment = makeIncrementer()
increment(7)
```
- A function can take **another function as one of its arguments.**
```swift
func hasAnyMatches(list: [Int], condition: (Int) -> Bool) -> Bool {
    for item in list {
        if condition(item) {
            return true
        }
    }
    return false
}
func lessThanTen(number: Int) -> Bool {
    return number < 10
}
var numbers = [20, 19, 7, 12]
hasAnyMatches(list: numbers, condition: lessThanTen)
```
- Functions are actually a special case of closures: blocks of code that can be called later. The **code in a closure** has access to things like variables and functions that were available in the scope where the closure was created, even if the closure is in a different scope when it’s executed — you saw an example of this already with nested functions. You can write **a closure without a name by surrounding code with braces ({}). Use in to separate the arguments and return type from the body.**
```swift
var numbers = [20, 19, 7, 12]
let mappedNumbers = numbers.map({ (number: Int) -> Int in
    let result = 3 * number
    return result
})
print(mappedNumbers)
```
- You have several options for writing closures more concisely. When **a closure’s type is already known**, such as the callback for a delegate, you can **omit the type of its parameters, its return type, or both.** Single statement closures implicitly return the value of their only statement.
```swift
let mappedNumbers = numbers.map({ number in 3 * number })
print(mappedNumbers)
// Prints "[60, 57, 21, 36]"
```
- You can refer to parameters by number instead of by name — this approach is especially useful in very short closures. A closure passed as the last argument to a function can appear immediately after the parentheses. When a closure is the only argument to a function, you can omit the parentheses entirely.
```swift
let sortedNumbers = numbers.sorted { (s1: Int, s2: Int) -> Bool in
    return s1 > s2
}
let sortedNumbers = numbers.sorted { $0 > $1 }
print(sortedNumbers)
// Prints "[20, 19, 12, 7]"
```
- Use class followed by the class’s name to create a class. Create an instance of a class by putting parentheses after the class name. Use dot syntax to access the properties and methods of the instance. This version of the Shape class is missing something important: an initializer to set up the class when an instance is created. **Use init to create one.**
- **Use deinit to create a deinitializer** if you need to perform some cleanup before the object is deallocated.
- In the setter for perimeter, the **new value has the implicit name newValue.**
- If you don’t need to compute the property but still need to provide code that’s run before and after setting a new value, **use willSet and didSet.** The code you provide is run any time the value changes outside of an initializer. 
- When working with optional values, you can **write ? before operations like methods, properties, and subscripting.** If the value before the ? is nil, everything after the ? is ignored and the value of the whole expression is nil. Otherwise, the optional value is unwrapped, and everything after the ? acts on the unwrapped value. In both cases, the value of the whole expression is an optional value.
```swift
let optionalSquare: Square? = Square(sideLength: 2.5, name: "optional square")
let sideLength = optionalSquare?.sideLength
```
- In Swift, rawValue is used in the context of enumerations (enums) to **represent the underlying value of an enumeration case.**In fact, in cases where there isn’t a meaningful raw value, you don’t have to provide one.
```swift
enum ServerResponse {
    case result(String, String)
    case failure(String)
}


let success = ServerResponse.result("6:00 am", "8:09 pm")
let failure = ServerResponse.failure("Out of cheese.")


switch success {
case let .result(sunrise, sunset):
    print("Sunrise is at \(sunrise) and sunset is at \(sunset).")
case let .failure(message):
    print("Failure...  \(message)")
}
// Prints "Sunrise is at 6:00 am and sunset is at 8:09 pm."
```
- Structures support many of the same behaviors as classes, including methods and initializers. **One of the most important differences between structures and classes is that structures are always copied when they’re passed around in your code, but classes are passed by reference.**
```swift
// 这里是enum类型的实际用例 ———— 一副牌的创建。
enum Suit {
    case spades, hearts, diamonds, clubs

    func simpleDescription() -> String {
        switch self {
        case .spades:
            return "spades"
        case .hearts:
            return "hearts"
        case .diamonds:
            return "diamonds"
        case .clubs:
            return "clubs"
        }
    }
}

enum Rank: Int {
    case ace = 1
    case two, three, four, five, six, seven, eight, nine, ten
    case jack, queen, king

    func simpleDescription() -> String {
        switch self {
        case .ace:
            return "ace"
        case .jack:
            return "jack"
        case .queen:
            return "queen"
        case .king:
            return "king"
        default:
            return String(self.rawValue)
        }
    }
}

struct Card {
    var suit: Suit
    var rank: Rank

    func simpleDescription() -> String {
        return "The \(rank.simpleDescription()) of \(suit.simpleDescription())"
    }
}

func generateDeck() -> [Card] {
    let suits: [Suit] = [.spades, .hearts, .diamonds, .clubs]
    let ranks: [Rank] = [.ace, .two, .three, .four, .five, .six, .seven, .eight, .nine, .ten, .jack, .queen, .king]
    
    var deck: [Card] = []
    
    for suit in suits {
        for rank in ranks {
            deck.append(Card(suit:suit, rank:rank))
        }
    }
    
    return deck
}

// Example usage
let deck = generateDeck()
for card in deck {
    print(card.simpleDescription())
}

```
- concurrency: aysc/await/actor/task/task group
- protocol & extention: mutating for structure
- Error handling: throw/throws/try/catch/
- generic fucntion or type <>

读完之后几个最奇怪的问题是：
- 怎么还允许这种数据类型？ upc(Int, Int, Int, Int)以及qrCode(String)
```swift
enum Barcode {
    case upc(Int, Int, Int, Int)
    case qrCode(String)
}
```
    - 回答： 都是元组。 在 Swift 中，元组（Tuple）是一种将多个值组合成一个复合值的数据类型。元组中的值可以是任意类型，并且不要求是相同类型。元组非常适合用于临时组合多个相关值。
- Swift有3种collection types：array, set, dictionary。[详见官网](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/collectiontypes)

元组和字典的区别
```swift
// 元组示例
let person = (name: "John", age: 30)
print("Name: \(person.name), Age: \(person.age)")

// 字典示例
var ages = ["John": 30, "Jane": 25]
print("John's age: \(ages["John"]!)")
ages["John"] = 31 // 更新值
print("John's new age: \(ages["John"]!)")
ages["Alice"] = 28 // 添加新键值对
print("Alice's age: \(ages["Alice"]!)")
```




