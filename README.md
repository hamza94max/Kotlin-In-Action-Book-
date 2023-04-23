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
