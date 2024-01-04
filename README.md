# THE SCALA PROGRAMMING LANGUAGE

**Basics of Scala programming language**

Welcome to the world of Scala, a versatile and powerful programming language that seamlessly blends object-oriented and functional programming paradigms. Whether you're a seasoned developer or just starting your programming journey, Scala has something unique to offer.

**Table of Contents:**

- [A Scalable Language](#a-scalable-language)
- [Variables in Scala](#variables-in-scala)
- [Strings](#strings)
- [Operating with Operators](#operating-with-operators)
- [Collections](#collections)
- [Control Structures](#control-structures)
- [Functions](#functions)
- [Classes and Objects](#classes-and-objects)
- [Sources](#sources)

## A Scalable Language

  ### What is Scala?
   "Scala is a general-purpose programming language providing support for both object-oriented programming and functional programming, and a strong static type system. Designed to be concise, many of Scala's design decisions aimed to address criticisms of Java."  [Source](https://en.wikipedia.org/wiki/Scala_(programming_language))
  
  ### Why use Scala?
   The first answer to "Why use Scala?" is in its name: Scala stands for **SCA**lable **LA**nguage. It is designed to grow with the demands of its users, from writing small scripts to building massive systems for data processing, distributed computing, and more.

   - _Scalability_: As the name suggests, Scala is scalable. It can seamlessly adapt to the evolving needs of your project, whether you're writing a quick script or developing complex, data-intensive applications.

   - _Combination_ of Paradigms: Scala supports both object-oriented and functional programming, offering the best of both worlds. This flexibility allows developers to choose the approach that best suits their problem.

   - _Static Typing_: Scala has a strong static type system, catching errors at compile-time rather than runtime, providing robustness to your code.

  ### Who uses Scala?
   The most common job titles you'll see are variants of software engineer, and data engineer. You'll also see data scientist and ML engineer more frequently as companies in all industries realize the challenges of analyzing big data. These companies are adopting Scala alongside data processing tools like Apache Spark.

## Variables in Scala
  "Variables are nothing but reserved memory locations to store values. This means that when you create a variable, you reserve some space in memory." [Source](https://www.tutorialspoint.com/scala/scala_variables.htm)

  ### Declaring a Variable

   In Scala, variables are used to store and manipulate data. There are two main types of variables: __`val`__ and __`var`__.
     
   The general format for daclaring a variable in scala is:

  ```Scala
    keyword variableName: DataType = Initial Value
   ```

   Where the `keyword` is one of the following:
   
   - `val` _(value)_: value cannot be changed after initialization, it's __immutable__
      
  ```scala 
     val x: Int = 10
  ```

   - `var` _(variable)_: value can be changed after initialization, it's __mutable__
      
  ```scala
     var y: String = "Hello"
  ```

  ### Data Types

   In Scala, every value has a type and each type is part of a type hierarchy. In a type hierarchy, the more generic types are at the top and as you go lower in the hierarchy, the types get more specific. Each type has a requirement of its own along with the requirements of all the types above it in the hierarchy.

   ```
    Any
    ├── AnyVal
    │  ├── Int
    │  ├── Long
    │  ├── Double
    │  ├── Float
    │  ├── Long
    │  ├── Char
    │  ├── Boolean
    │  ├── Byte
    │  └── Unit
    ├── AnyRef (or Object)
    │  ├── String
    │  ├── List
    │  ├── Set
    │  ├── Map
    │  ├── Function
    │  ├── Tuple
    │  ├── Option
    │  ├── Iterable
    │  └── ...
    ├── Null
    └── Nothing
  ```

   NB: 

   - `Null` is a subtype of all reference types (including _AnyRef_).
   - `Nothing` is a subtype of all types, both reference and value types.

  ### Type Inference

   Scala has a powerful type inference system, allowing you to omit explicit type declarations when the compiler can infer the type:

   - Scala compiler automatically determines the data type of the expression and assigns to the variable based on its value. It is called as *__type*
   - If you don’t specify the data type of a variable explicitly then Scala will infer its type from the initial value assigned to that variable.
   
   ```scala
    keyword variableName: DataType = Initial Value
                        ||
    keyword variableName = Initial Value
   ```

   Example:
   ```scala
    (val x: Int = 10) == (val x = 10)
    (var y: String = "Hello") == (var y = "Hello")
   ```

   Type inference enhances code readability and reduces the need for explicit type annotations.

  ### Type Casting

  Type casting, also known as type conversion, is the process of converting a value from one data type to another. In Scala, type casting can be explicit or implicit, depending on the scenario.

  #### Type Casting Flow:

  In Scala, the type casting flow follows a hierarchy, and explicit casting is needed when moving from a less specific type to a more specific one:

  ```
  Byte —> Short —> Int —> Long —> Float —> Double
                      ^
                      | 
                    Char
  ```

  #### Explicit Type Casting:

  To explicitly cast a value from one type to another, you use the `to*` methods provided by each numeric type:

  ```scala
  val intValue: Int = 42
  val doubleValue: Double = intValue.toDouble // Explicitly casting Int to Double
  ```

  In the example above, the `toDouble` method is used to explicitly cast an `Int` to a `Double`.

  #### Implicit Type Conversion:

  Scala also supports implicit type conversion in certain cases, such as when assigning a value to a variable of a different type:

  ```scala
  val intNumber: Int = 42
  val doubleNumber: Double = intNumber // Implicit conversion from Int to Double
  ```

  In this case, Scala automatically converts the `Int` value to a `Double` because it's a widening conversion and doesn't result in loss of precision.

  #### Avoiding Type Casting Pitfalls:

  While type casting is a powerful tool, it's important to be cautious to avoid runtime errors. Always ensure that the conversion makes sense in the context of the program, and consider potential loss of information when narrowing types.

  ```scala
  val doubleValue: Double = 42.5
  val intValue: Int = doubleValue.toInt // Be aware of potential loss of decimal precision
  ```

## Strings
  ### Declaring a String:

   Explicitly mentioning the data type:
  
   ```scala
   val myFirstString String = "I'm a string"
   ```

   Using type inference:
   
   ```scala
   val mySecondString = "Type Inference is Cool!"
   ```

  ### Using Java’s String Methods:
   
   Length of a String:

   ```scala
   val stringVar = "What is the length of this string?" 
   println(stringVar.length())
   ```

   String Concatenation:

   ```scala
   println("Hello " + "Data")   
   println("This is the integer " + 5)

   val string1 = "Hello" 
   val string2 = "Data"
   println(string1.+(string2))

   val aFloat = 1.5F
   println("This is the floating point " + aFloat)
   ```

  ### String Interpolation:

   The __s__ String Interpolator
   
   Formats:
   ```scala
   s"Optional String $VariableIdentifier Optional String" 
   
   s"Optional String ${Expression} Optional String"
   ```

   Example:
   ```scala
   val name = "James"
   val age = 30
   println(s"$name is $age years old")  // "James is 30 years old"

   println(s"2 + 2 = ${2 + 2}")   // "2 + 2 = 4"
   ```

   The __f__ String Interpolator

   ```scala
   f"String $VariableIdentifier%FormatSpecifier String"
 
   %FormatSpecifier == %FlagWidth.PrecisionConversion-Character
   ```

   Flag:

   |Flag|Use|
   |---|---|
   |-|left justify|
   |+|add a + sign|
   |0|add padded zeros|
   |,|separator|
   
   Conversion-Characters:

   |Character|Use|
   |---|---|
   |s|Strings|
   |d|decimal integers|
   |f|floating-point numbers|
   |t|date/time values|

   Example:
   ```scala
   val pi = 13.14159F
   print(f"The value of pi is $pi%1.2f") // The value of pi is 3.14

   val testWidth = 123
   println(f"Without specifying the width, we get $testWidth")  // Without specifying the width, we get 123
   println(f"With specifying the width, we get $testWidth%-10d") // With specifying the width, we get        123
   ```

   The __row__ String Interpolator:

   ```scala
   row"Optianal String EscSeq Optional String"
   ```

   Escape Sequence:

   |EscSeq|Use|
   |---|---|
   |\n|newline|
   |\r|carriage return|
   |\t|tab|
   |\b|represents a backspace character|
   |\\\ |backslash|
   |\\"|double quote|
   |\\'|single quote|
   |\uAAAA|represents the character with the Unicode value AAAA|

   Example:
   ```scala
   val filePath = "C:\\Users\\user\\Documents\\file.txt"
   val rawString = raw"This is a raw string with backslashes: $filePath"

   println(rawString) // This is a raw string with backslashes: C:\Users\user\Documents\file.txt
   ```

  ### Comparing Strings:

   ```scala
   string1 == string2
   string1.equals(string2)
   string1.equalsIgnoreCase(string2) string1.matches(regex)
   string1.compareTo(string2)
   ```
  ### Updating Strings:

   Finding patterns:
   ```scala
   val match1 = Regex.findFirstIn(stringToFindExpression) 
   match1.foreach(println)

   val match2 = Regex.findAllIn(stringToFindExpression) 
   match2.foreach(println)
   ```

   Splitting string:
   ```scala
   val names = "achraf, mohamed, ahmed".split(",") 
  names.foreach(println)
   ```

   Replacing patterns
   ```scala
   String.replaceFirst("SearchExpression","ReplaceExpression") 
   Regex.replaceFirstIn("SearchString","ReplaceExpression") 
   String.replaceAll("SearchExpression","ReplaceExpression") 
   Regex.replaceAllIn("SearchString","ReplaceExpression")
   ```

## Operating with Operators 
  ### Functions/Methodes:
   - Built-In Functions:
     - Built-in functions are functions which are predefined by Scala and are part of their libraries.
     - All we have to do to use them is call their function name.
     - Built-in functions are known as methods. 

     Examples:
     - println 
     - sorted 
     - map
     - filter 
     - reduce 
     - groupBy
     - ...

   - User-Defined Functions:
     - User-defined functions are functions that users create themselves. We will cover this in another chapter

  ### Calling a Function:
   - In scala, calling a method is done using the dot operator (.) followed by the method's name. It's the _ordinary method call_:
    ```scala
     objectName.methodName(arguments)
    ```
   - There is another way to call a function, it is by using _operator notation_: 
    ```scala
     objectName methodName arguments
    ```

  ### Operators:
   - Operators are Methodes:
   

  ### Methods vs Functions
        1. A method can contain expressions that return values while a function cannot.
        2. A method has an implicit this parameter whereas a function does not.
        3. A method can take parameters but it must always end with a semicolon or curly braces.
        Whereas a function ends with either a semicolon or curly brace depending on whether it returns value or not.
        4. A method can also return values.
        5. If you want to make your code more readable then instead of writing a method you can write a function.
        5. A method can only perform operations on objects.
        6. A method can access private members of its class.
        7. A method can modify the state of its class.
        8. A method can throw exceptions.
        9. A method can override another method from superclass.
        10. A method can be called without creating any instance of the class.
        11. A method can be used inside other classes.
        12. A method can be used outside the class where they were declared.
        13. A method can be used within itself.
        14. A method can be used recursively.
        15. A method can be passed as argument to another method.
        16. A method can be returned as result from another method.
        17. A method can be assigned to variables.
        18. A method can be stored in collections like List and Map.
        19. A method can be used as anonymous inner class.
        20. A method can have default value for parameters.
        21. A method can have multiple types for single parameter.
        22. A method can have vararg parameters which means zero or more than one parameters.
        23. A method can have optional parameters which means you don’t need to provide all parameters when calling them.


## Collections


## Control Structures 


## Functions


## Classes and Objects


## Sources