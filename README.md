# Kotlin-In-Action-Book-

### Advantages of kotlin:
Kotlin is pragmatic, safe, concise, and interoperable, meaning it focuses on using proven
solutions for common tasks, preventing common errors such as `NullPointerException`s, supporting compact and easy-to-read code, and unrestricted 



### Notes:

## ch 1 :

```kotlin
val x = 1
```
* Kotlin automatically determines that its type is Int. The ability of the compiler to determine
types from context is called _**type inference**_

* Most of the code that would lead to a NullPointerException in
Java fails to compile in Kotlin, ensuring that you fix the error before the application gets
to your


## ch 2 :

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

## ch 3 : Defining and calling functions-:

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





