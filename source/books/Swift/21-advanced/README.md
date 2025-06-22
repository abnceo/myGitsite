# 教程 appcoda.com

### from https://www.appcoda.com/learnswift/
- you can hold the option key, and click any variable name to reveal the variable type, deduced by the compiler.
- press shift+command+enter to execute the code
- To reveal the error details, you can refer to the debug area/console. If the console doesn't show up in your Playground, click the debug area button at the top-right corner.
- String interpolations is the recommended way to build a string from multiple types. You wraps the variable for string conversion in parentheses, prefixed by a backslash.
    ```swift
    var totalPriceMessage = "The price of the book is $ \(totalPrice)"
    ```
- Swift has a very handy range operator (...) that defines a range from lower bound to upper bound. For example, 5000...9999 defines a range that runs from 5000 to 9999. For the first case, 10000... indicates a value that is great than 10000.
- Swift's for-in loop offers an alternate way to iterate over an array. The sample code snippet can be rewritten as follows:
    ```swift
    for index in 0...bookCollection.count - 1 {
        print(bookCollection[index])
    }
    ```
    ```swift
    for book in bookCollection {
        print(book)
    }
    ```
- You have to do some checkings before using the optional variable. This is how optionals can prevent you from writing bad code. Whenever you need to access an optional variable, Xcode forces you to perform verification to find out whether the optional has a value.
    - Forced Unwrapping
    ```swift
    if jobTitle != nil {
        var message = "Your job title is " + jobTitle!
    }
    // When you need to access the value of jobTitle, you add an exclamation mark (!) to the end of the optional variable. This exclamation mark is a special indicator, telling Xcode that you ensure the optional variable has a value, and it is safe to use it.
    ```
    - The other way is called optional binding, and it is the recommended way to work with optionals. At least, you do not need to use !.
    ```swift
    if let jobTitleWithValue = jobTitle {
        var message = "Your job title is " + jobTitleWithValue
    }
    // Do you have to give a new name for the temporary constant? No, you can actually use the same name.
    if let jobTitle = jobTitle {
        var message = "Your job title is " + jobTitle
    }
    // Even though the names are the same, there are actually two variables in the code above. jobTitle in black is the optional variable, while jobTitle in blue is the temporary constant to be assigned with the optional value.
    ```