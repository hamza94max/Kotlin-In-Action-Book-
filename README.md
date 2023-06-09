# Kotlin-In-Action-Book-

### Advantages of kotlin:
Kotlin is pragmatic, safe, concise, and interoperable, meaning it focuses on using proven
solutions for common tasks, preventing common errors such as `NullPointerException`s, supporting compact and easy-to-read code, and unrestricted 



### Notes:

<details close>
<summary>ch 1 : Intro to kotlin basics</summary>

```kotlin
val x = 1
```
* Kotlin automatically determines that its type is Int. The ability of the compiler to determine
types from context is called _**type inference**_

* Most of the code that would lead to a NullPointerException in
Java fails to compile in Kotlin, ensuring that you fix the error before the application gets
to your

</details>

<details close>
<summary>ch 2 : Defining</summary>

* **val** (from value)—Immutable reference. A variable declared with val can’t be
reassigned after it’s initialized. It corresponds to a **final** variable in Java. 

* **var** (from variable)—Mutable reference. The value of such a variable can be changed. This declaration corresponds to a regular (**non-final**) 

* Using **immutable references**, immutable objects, and
functions without side effects makes your code closer to the functional style.

```kotlin
class Person(
val name: String,
var isMarried: Boolean
)
```

* `name` Read-only property: generates a field and a trivial getter <br>
* `isMarried` Writable property: a field, a getter, and a set
<br>
* The concise syntax 1..5 creates a range. Ranges and progressions allow Kotlin to use a
uniform syntax and set of abstractions in for loops and also work with the in and !in operators that check whether a value belongs to a range.

```kotlin
val percentage = if (number in 0..100) number
```
 ### Lazy Keyword:
 
In Kotlin, `lazy` is a function that is used to create a lazily initialized property.
 A lazily initialized property is a property that is computed or initialized only when it is accessed for the first time, not when the object is created. 
 
 
 
 
</details>



<details close>
<summary>ch 3 : Defining and calling functions-:</summary>

* Kotlin doesn’t have its own set of collection classes. All of your
existing knowledge about Java collections 

* **joinToString()** :

```java
/* Java */
collection.joinToString(/* separator */ " ", /* prefix */ " ", /* postfix */ ".");
```
```kotlin
collection.joinToString(separator = " ", prefix = " ", postfix = ".")
```

_**Note: in a call, you should also specify the names for all the arguments after that, to avoid
confusion.**_


#### extension functions:

```kotlin
package strings

fun String.lastChar(): Char = get(length - 1)

```

```kotlin
import strings.lastChar
val c = "Kotlin".lastChar() // n
```

#### Working with maps-: 

```kotlin 
val map = mapOf(1 to "one", 7 to "seven", 53 to "fifty-three")
```

**NOTE:** **_The word to in this line of code isn’t a built-in construct, but rather a
method invocation of a special kind, called an_** **infix call**

#### Strings: 
```kotlin
 println("12.345-6.A".split("\\.|-".toRegex()))
[12, 345, 6, A]
``` 

For instance, in Kotlin you use an extension function toRegex to convert a string into a **regular expression**


#### fully example for extenstion functions to avoid duplicated
``` kotlin
class User(val id: Int, val name: String, val address: String)
fun saveUser(user: User) {
fun validate(value: String, fieldName: String){
  if (value.isEmpty()) {
  throw IllegalArgumentException(
  "Can't save user ${user.id}: " +
  "$fieldName is empty")
  }}
validate(user.name, "Name")
validate(user.address, "Address")
// Save user to the database
}
>>> saveUser(User(1, "", ""))
java.lang.IllegalArgumentException: Cannot save user 1: Name is empty
```


**NOTE: Local functions help you structure your code more cleanly and eliminate duplication**

</details>



<details close>
<summary>ch 4 : Classes-:</summary>

* All classes and methods that aren’t specifically intended to be overridden in subclasses need to be
explicitly marked as **final**


* If you want to allow the creation of subclasses of a class, you need to mark the class
with the open modifier. In addition, you need to add the open modifier to everyproperty
or method that can be overridden: //AU: I’ve added blank lines between the code lines to
make room for the annotations. OK? TT

```kotlin
open class RichButton : Clickable { //1
fun disable() {} //2
open fun animate() {} // 3
override fun click() {} //4
}
```
1-This class is **open**: others can inherit from it. <br>
2-This function is **"final"**: you can’t override it in a subclass. <br>
3-This function is **open**: you may override it in a subclass<br>
4-This function overrides an **open** function and is open as well.<br>

![book 1](https://user-images.githubusercontent.com/54688005/234026276-9615cccd-892f-417e-bc1d-14e108fd9c01.PNG)
<br>
![book 2](https://user-images.githubusercontent.com/54688005/234026312-ba6c584a-af86-4147-9aab-f3038d8c46e8.PNG)

<br>

* **Inner Class** : 
 the inner keyword is used to mark a nested class as an inner class. An inner class can access members of its outer class, including private members, and has a reference to an instance of its outer class.
 
```kotlin
class OuterClass {
    private val outerProperty = "Outer property"
    
    inner class InnerClass {
        fun printOuterProperty() {
            println(outerProperty) // output: Outer property
        }
    }
}
```




_Usecases in Android: ViewHolder class in RecyclerView adapter_ 


* **Sealed Class** : 

You mark a superclass with the sealed modifier, and that restricts the possibility of creating subclasses. 
All the direct subclasses must be nested in the superclass

**can only be subclassed within the same file where it is declared.**

* **companion**:

. If you do that, you gain the ability to access the methods and properties of
that object directly through the name of the containing class, without specifying the name
of the object explicitly. The resulting syntax looks exactly like static method invocation
in Java. Here’s a basic example showing the syntax:
```kotlin
class A {
 companion object{
  fun bar() {
  println("Companion object called")
  }
 }
}
```
>>> A.bar()<br>
Companion object called

</details>

<details close>
<summary>ch 5 : Lambdas-: more concise and readable</summary>


* This is program to find the oldest person in list using lambdas (maxBy)

```kotlin 
 val people = listOf(Person("Alice", 29), Person("Bob", 31))
 println(people.maxBy { it.age })
 // output : Person(name=Bob, age=31)
```


### Lambda expression syntax :

```kotlin 
val sum = { x: Int, y: Int -> x + y }
 println(sum(1, 2))  // 3
 ```
 
 ![3](https://user-images.githubusercontent.com/54688005/235179218-2c3040e0-57a6-417c-a597-6ff367b0df30.PNG)
 
 ### filter function:
 ```kotlin 
 data class Person(val name: String, val age: Int)
 
 val list = listOf(1, 2, 3, 4)
 list.filter { it % 2 == 0 }
 // output => [2, 4]
```
 
 ### map function:-
 The filter function can remove unwanted elements from a collection, but it doesn’t
change the elements. Transforming elements is where **map** comes into play

```kotlin 
val list = listOf(1, 2, 3, 4)
 list.map { it * it }
// output => [1, 4, 9, 16]
```


### all & any :
```kotlin 
val people = listOf(Person("Alice", 27), Person("Bob", 31))
println(people.all(canBeInClub27))
/ output => false
```

If you need to check whether there’s at least one matching element, use any:

```kotlin 
println(people.any(canBeInClub27))
// true
```

**Note that !all (not-all), !any (not-any) can be replaced with any with a negated condition and vice versa**

 
 ### groupBy :
 For example, you want to group people of the same age together. It’s convenient
to pass this quality directly as a parameter. The groupBy function can do this for you 
 ```kotlin 
  val people = listOf(Person("Alice", 31),
  Person("Bob", 29), Person("Carol", 31))
  println(people.groupBy { it.age })
 
 // output => {29=[Person(name=Bob, age=29)],
// 31=[Person(name=Alice, age=31), Person(name=Carol, age=31)]
 ```
 so the result type is Map<Int, List<Person>>
 
 
 
 ### flatMap:
 The **flatMap** function does two things: at first it transforms (or maps) each element
to a collection according to the function given as an argument, and then it combines (or flattens) several lists into one
 
 ```kotlin 
 val strings = listOf("abc", "def")
 println(strings.flatMap { it.toList() })
// output => [a, b, c, d, e, f]
 ```
 
<img src="https://github.com/hamza94max/Kotlin-In-Action-Book-/assets/54688005/8552f340-408d-4095-af9b-d0a20816b30c" alt="Alt Text" width="550" height="250">

 
 ### sequences:
 The Kotlin standard library reference says that both filter and map return a list. That means this chain of calls will create two lists: one to hold the results of the **filter** function and another for the results of map.
 This isn’t a problem when the source list contains two elements, but it becomes much less efficient if you have a million.
 To make this more efficient => you can convert the operation so it uses sequences instead of using collections directly:
 
 ```kotlin
 people.asSequence()
.map(Person::name)
.filter { it.startsWith("A") }
.toList()
 ```
 
 ### The `with` function:
 use to perform multiple operations on the same object without repeating its name (make it short)
 
 
 see the diff between two codes 
 1. 
 ```kotlin
 fun alphabet(): String {
    val result = StringBuilder()
    for (letter in 'A'..'Z') {
    result.append(letter)
    }
    result.append("\nNow I know the alphabet!")
    return result.toString()
 }
 ```
 
 2. 
 ```kotlin
 fun alphabet(): String {
   val stringBuilder = StringBuilder()
   return with(stringBuilder){
    for (letter in 'A'..'Z'){
     this.append(letter)
   }
   append("\nNow I know the alphabet!")
   this.toString()
}}
```
 
 
 ## The `apply` function:-
 
 As you can see, apply is an extension function, works almost exactly the same as with; the only difference is that
**apply()** always returns the object passed to it as a parameter
 
 ```kotlin
 fun alphabet() = StringBuilder().apply{
  for (letter in 'A'..'Z') {
   append(letter)
   }
  append("\nNow I know the alphabet!")
  }.toString()
 ```
 
 // end of Ch 5
 
 
</details>


<details close>
<summary>ch 6 : The Kotlin type system </summary>

 
 ## Nullability:-
**Nullability** is a feature of the Kotlin type system that helps you avoid `NullPointerException` errors.

**Kotlin convert this problem from runtime errors to compile errors**
 
 ![gg](https://github.com/hamza94max/Kotlin-In-Action-Book-/assets/54688005/684be86e-ee75-424d-858f-af94b7129f7e)

a type without a question mark `?` denotes that variables of this type can’t store null references.
 
 
 ### Safe call operator: **?.**
 
 `?.` It allows you to combine a `null` check and a method call into a single operation. 
 For example, the expression `s?.toUpperCase()` is equivalent to the following, more cumbersome one: 
 `if (s != null) s.toUpperCase() else null`
 
 
 ### Operator: `?:`
 
 ```kotlin
 fun foo(s: String?) {
val t: String = s ?: ""  // If "s" is null, the result is an empty string
}
 ```
 
 ### Operator: `as?`
 
 The `as?` operator tries to cast a value to the specified type and returns `null` if the
value doesn’t have the proper type
 
 ### Not_null assertions: `!!`
 
  It’s represented by a double exclamation mark and converts any value to a non-null type
 
 
 ### The `let` function:-
 to deal with a nullable argument that should be passed to a function that expects a **non-null** parameter
 
 ```kotlin
 email?.let { email -> sendEmailTo(email) } == if (email != null) sendEmailTo(email)
 ```

 
 ![6](https://github.com/hamza94max/In-MotionSystem/assets/54688005/f59e8e90-eee8-4a58-9eda-14c5cf589690)

 
 ### Primitive types: Int, Boolean, and more :-
 Kotlin doesn’t distinguish between primitive types and wrapper types (ex: `Integer`)
 You always use the same type (for example, `Int`)
 
 
 ### The Unit type: Kotlin’s "void" :
 The `Unit` type in Kotlin fulfills the same function as `void` in Java. 
 It can be used as a return type of a function that has nothing interesting to return:
 
 ```kotlin
 fun f(): Unit { ... }  == fun f() { ... }
```
 
 ### Collections :
 ![7](https://github.com/hamza94max/In-MotionSystem/assets/54688005/9efd4739-3743-4d9d-adbe-da42a5c9920e)
<br>
 
 ![8](https://github.com/hamza94max/In-MotionSystem/assets/54688005/3aacaa47-2009-4690-b204-6ba105903dbb)
<br>
 
 ![9](https://github.com/hamza94max/In-MotionSystem/assets/54688005/e4be3fc0-60eb-417a-bc10-39df0197baff)



</details>



<details close>
<summary>ch 7 : Operator overloading and other conventions </summary>
 
 
 ### Overloading binary arithmetic operations:-
 
 ``` kotlin
 data class Point(val x: Int, val y: Int){
   operator fun plus(other: Point): Point{
     return Point(x + other.x, y + other.y)
  }
}
 ```
** NOTE: the `operator` keyword to declare the plus function. All functions used to overload operators need to be marked with that keyword** 
 
 #### another example 
 ```kotlin
 operator fun Point.unaryMinus(): Point{ 
 return Point(-x, -y)
}
>>> val p = Point(10, 20)
>>> println(-p)
Point(x=-10, y=-20)
 ```
 
 
 ### Equality operators: equals:-
 Note how you use the identity equals operator **(===)** to check whether the parameter
to equals is the same object as the one on which equals is called.
 
 ### Ordering operators: compareTo:-
 ![gg](https://github.com/hamza94max/Kotlin-In-Action-Book-/assets/54688005/ac8f85e9-568a-4b63-9cf9-630c66693822)

 
 ### Lazy delegated properties :
 
==> creating part of an object on demand, **when it’s accessed for the first time**
 
 
  #### what is the benefit of lazy ? 
 benefits of using the lazy keyword:

1.**Efficient resource utilization**: With lazy initialization, resources are only allocated when they are actually needed
 
2.**Thread-safe initialization:** The lazy delegate ensures that the initialization of the property is thread-safe. 

3.**Cleaner code:** The lazy keyword helps to simplify code by encapsulating the lazy initialization logic in a concise and readable manner

4.**Support for immutable properties**: The lazy keyword can be used with val properties
 
 
 so you can use it together with the `by` keyword to create a delegated
property. The parameter of lazy is a lambda that it calls to initialize the value. The lazy
function is thread-safe by default
 
 ``` kotlin 
 val emails by lazy { loadEmails(this)}
 ```
 --------------------------------------------------------------------------------------------------------------------------------------

 
 
 
 </details>
 
 
 
 
 
 
 
 
 
 
 
 

