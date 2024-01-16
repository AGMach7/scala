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

   The __s__ String Interpolator: Prepending s to any string literal allows the usage of variables directly in the string.
   
   Formats:
   ```scala
   s"Optional String $VariableIdentifier Optional String" 
   
   s"Optional String ${Expression} Optional String"
   ```

   Example:
   ```scala
   val name = "James"
   val bDay = 2001
   println(s"$name is ${2024-bDay} years old")  // "James is 23 years old"
   ```

   The __f__ String Interpolator: Prepending `f` to any string literal allows the creation of simple formatted strings, similar to `printf` in other languages. When using the `f` interpolator, all variable references should be followed by a `printf`-style format string, like `%d`
   
   Formats:
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

   The __row__ String Interpolator: The raw interpolator is similar to the `s` interpolator except that it performs no escaping of literals within the string
   
   Format:
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
   val sString = s"a\tb"
   val rawString = raw"a\tb"

   println(sString)  // a    b
   println(rawString) // a\tb
   ```

  ### Comparing Strings:

   In Scala, string comparison involves various methods for assessing equality, considering case sensitivity, and utilizing regular expressions:

   - Check if two strings are equal:
   ```scala
   string1 == string2

   // Example: 
   "hello" == "hello" // true
   ```
   - Use the equals methode for equalitu comparison:
   ```scala
   string1.equals(string2)

   // Example: 
   "Hello".equals("hello") // false
   ```
   - Rerform  case-insensitive equality check:
   ```scala
   string1.equalsIgnoreCase(string2)

   // Example: 
   "Scala".equalsIgnoreCase("sCaLa") // true
   ```
   - Check if the string matches a regular expression:
   ```scala
   string1.matches(regex)

   // Example: 
   "12345".matches("\\d+") // true
   ```
   - Compare strings lexicographically:
   ```scala
   string1.compareTo(string2)

   // Example: 
   "apple".compareTo("banana") // -1
   ```

  ### Updating Strings:

   In the realm of string manipulation in Scala, the section on updating strings encompasses three essential operations: finding patterns, splitting strings, and replacing patterns:

   - Finding patterns:
   ```scala
   // Find the first occurrence of a pattern in the string
   val match1 = Regex.findFirstIn(stringToFindExpression) 
   match1.foreach(println)

   // Find all occurrences of a pattern in the string
   val match2 = Regex.findAllIn(stringToFindExpression) 
   match2.foreach(println)
   ```

   - Splitting string:
   ```scala
   // Split the string using a specified delimiter
   val names = "achraf, mohamed, ahmed".split(",") 
  names.foreach(println)
   ```

   - Replacing patterns
   ```scala
   // Replace the first occurrence of a pattern in the string
   String.replaceFirst("SearchExpression","ReplaceExpression")

   // Replace the first occurrence of a pattern using a regex
   Regex.replaceFirstIn("SearchString","ReplaceExpression")

   // Replace all occurrences of a pattern in the string
   String.replaceAll("SearchExpression","ReplaceExpression")

   // Replace all occurrences of a pattern using a regex
   Regex.replaceAllIn("SearchString","ReplaceExpression")
   ```
## Operating with Operators

  ### Functions/Methods:

  - Built-In Functions:

    Built-in functions in Scala are predefined functions provided by the language and are part of its standard libraries. These functions, often referred to as methods, cover a wide range of functionalities and operations. Users can easily utilize these functions by invoking their names. Some common examples include:

    - **`println`:** Outputs information to the console.
    - **`sorted`:** Sorts elements in a collection.
    - **`map`:** Applies a function to each element in a collection and returns a new collection.
    - **`filter`:** Selects elements from a collection based on a specified condition.
    - **`reduce`:** Aggregates elements in a collection to a single value using a specified operation.
    - **`groupBy`:** Groups elements in a collection based on a provided key function.
    - ...

  - User-Defined Functions:

    User-defined functions are functions created by users themselves. These functions are defined by the user to perform specific tasks or operations, providing a way to extend the functionality of the language beyond its built-in capabilities. User-defined functions will be covered in more detail in another chapter.

  ### Calling a Function:

  In Scala, calling a method involves using the dot operator (.) followed by the method's name, representing the ordinary method call. The syntax is as follows:

  ```scala
  objectName.methodName(arguments)
  ```

  Additionally, Scala supports another way of calling functions known as the **operator notation**:

  ```scala
  objectName methodName arguments
  ```

  In the operator notation, the method name is placed directly after the object or expression, and the parentheses are omitted. This notation offers a more concise and expressive way of calling methods in certain situations, contributing to Scala's flexibility and readability. Both the ordinary method call and operator notation are valid ways to invoke functions in Scala, providing developers with options based on their preferences and the context of the code.

  Example:
  ```Scala
  val numbers = List(1, 2, 3, 4, 5)

  // Calling the reduce method in the ordinary way
  val sum1 = numbers.reduce((a, b) => a + b)
  println(s"Sum using ordinary method call: $sum1") //Sum using ordinary method call: 15

  // Calling the reduce method using operator notation
  val sum2 = numbers reduce ((a,b) => a + b)
  println(s"Sum using operator notation: $sum2") //Sum using operator notation: 15
  ```

  ### Operators:
   Operators are Methodes! In Scala, operators are essentially methods. Unlike some other programming languages where operators are distinct from methods, Scala treats operators as syntactic sugar for method calls. This means that when you use an operator in Scala, you are actually calling a method with a special syntax.

   For example, the addition operation `+` is treated as a method call in Scala. Instead of a traditional operator, it is implemented as a method named `+`:
   
   ```scala
   val result = 3 + 5
   // In reality, it's the same as calling:
   // val result = 3.+(5)
   ```

   Here, the `+` operator is translated into a method call, and the expression is equivalent to `3.+(5)`.

   This design choice provides consistency in the language, making operators more flexible and extensible. It also aligns with Scala's emphasis on a unified object-oriented approach, **_`treating everything as an object and every operation as a method call`_**.

  ### Methods vs Functions:

  1. **Expression and Return:**
    - Both methods and functions in Scala can contain expressions that return values.

  2. **Implicit `this` Parameter:**
    - Methods have an implicit `this` parameter, while functions do not. This distinction is relevant when calling methods on instances.

  3. **Parameters and Syntax:**
    - Both methods and functions can take parameters. Methods must end with either a semicolon or curly braces. Functions end with a semicolon if they don't return a value, and with curly braces if they do.

  4. **Return Values:**
    - Both methods and functions can return values.

  5. **Readability:**
    - Both methods and functions contribute to code readability. The distinction here might be subjective.

  6. **Operations on Objects:**
    - Both methods and functions can perform operations on objects.

  7. **Access to Private Members:**
    - Both methods and functions can access private members of their classes.

  8. **Modify Class State:**
    - Both methods and functions can modify the state of their classes.

  9. **Throw Exceptions:**
    - Both methods and functions can throw exceptions.

  10. **Method Override:**
      - Both methods and functions can override another method from a superclass.

  11. **Instance Creation:**
      - Both methods and functions can be called without creating an instance of the class.

  12. **Usage in Other Classes:**
      - Both methods and functions can be used inside other classes.

  13. **Usage Outside Class:**
      - Both methods and functions can be used outside the class where they are declared.

  14. **Usage Within Itself:**
      - Both methods and functions can call themselves recursively.

  15. **Passed as Arguments:**
      - Both methods and functions can be passed as arguments to other methods/functions.

  16. **Returned as Result:**
      - Both methods and functions can be returned as results from other methods/functions.

  17. **Assigned to Variables:**
      - Both methods and functions can be assigned to variables.

  18. **Stored in Collections:**
      - Both methods and functions can be stored in collections like List and Map.

  19. **Used as Anonymous Inner Class:**
      - This point is more applicable to methods when used as SAM (Single Abstract Method) instances.

  20. **Default Parameter Values:**
      - Both methods and functions can have default values for parameters.

  21. **Multiple Types for Single Parameter:**
      - Both methods and functions can have parameters with multiple types.

  22. **Vararg Parameters:**
      - Both methods and functions can have varargs parameters.

  23. **Optional Parameters:**
      - Both methods and functions can have optional parameters using default values.

  In Scala, the distinction between methods and functions is less rigid than in some other languages. Functions are essentially objects and can be treated as first-class citizens, while methods are associated with specific instances of classes or objects. The choice between them often depends on coding style and the context in which they are used.

## Collections


## Control Structures 


## Functions


## Classes and Objects


## Sources

- [Official website](https://www.scala-lang.org/)
- [Latest version documentation](https://www.scala-lang.org/api/current/index.html)
- [Learn Scala | Scala Documentation](https://docs.scala-lang.org/)
- [educative](https://www.educative.io/courses/learn-scala-from-scratch)
- [tutorialspoint](https://www.tutorialspoint.com/scala/index.htm)
- [Learning Scala Programming - GitHub repo](https://github.com/PacktPublishing/Learn-Scala-Programming/tree/master)
- [Scala strings - GitHup repos](https://github.com/Baeldung/scala-tutorials/tree/master/scala-strings)
- [Cheatsheet - 1](https://docs.scala-lang.org/cheatsheets/index.html)
- [Cheatsheet - 2](https://gist.github.com/heathermiller/2ab9ef36910fdfdd20e9)
- [Scala Quick Reference v1.1](https://homepage.cs.uiowa.edu/~tinelli/classes/022/Fall13/Notes/scala-quick-reference.pdf)
- []()
- []()
- []()
