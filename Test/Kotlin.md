
## **1. What are the main features of Kotlin?**

**Kotlin** is a modern programming language fully interoperable with Java.

**Key Features:**

* Concise syntax → less boilerplate
* Null safety → avoids NullPointerException
* Interoperable with Java
* Functional programming support
* Extension functions
* Smart casts
* Coroutines for asynchronous programming

---

## **2. Difference between var, val, and const**

| Keyword | Description                          | Use Case                                  |
| ------- | ------------------------------------ | ----------------------------------------- |
| `var`   | Mutable variable                     | Can be reassigned                         |
| `val`   | Immutable variable                   | Read-only after initialization            |
| `const` | Compile-time constant, must be `val` | For constants at top-level or in `object` |

**Example:**

```kotlin
var name = "Aasim"    // Can be reassigned
val age = 25          // Cannot be reassigned
const val PI = 3.14   // Compile-time constant
```

---

## **3. What is a Kotlin data class?**

**Data class:** A class used to hold data, automatically provides `toString()`, `equals()`, `hashCode()`, and `copy()`.

**Syntax:**

```kotlin
data class User(val name: String, val age: Int)
```

**Advantages:**

* Reduces boilerplate
* Provides `componentN()` functions for destructuring
* Useful for DTOs / API models

---

## **4. Difference between `==` and `===` in Kotlin**

| Operator | Meaning                                        |
| -------- | ---------------------------------------------- |
| `==`     | Checks structural equality (values)            |
| `===`    | Checks referential equality (object reference) |

**Example:**

```kotlin
val a = "Hello"
val b = "Hello"
println(a == b)  // true (value)
println(a === b) // true/false (reference)
```

---

## **5. What is Kotlin null safety?**

**Null Safety:** Prevents NullPointerException by distinguishing nullable and non-nullable types.

**Syntax:**

* Non-nullable: `val name: String = "Aasim"` → cannot assign null
* Nullable: `val name: String? = null` → can assign null

**Safe call and Elvis operator:**

```kotlin
val length = name?.length ?: 0  // Returns 0 if name is null
```

---

## **6. What are Kotlin extension functions?**

**Extension functions** allow adding functions to existing classes without inheritance.

**Example:**

```kotlin
fun String.reverseText(): String {
    return this.reversed()
}

val text = "Kotlin"
println(text.reverseText())  // "niltok"
```

**Use case:**

* Add helper functions without modifying the original class

---

## **7. Difference between `open`, `abstract`, and `interface`**

| Keyword     | Description                                                        |
| ----------- | ------------------------------------------------------------------ |
| `open`      | Class can be inherited; methods can be overridden                  |
| `abstract`  | Cannot instantiate; abstract methods must be overridden            |
| `interface` | Defines contract; no constructor; can have default implementations |

**Example:**

```kotlin
open class A
abstract class B { abstract fun doSomething() }
interface C { fun doSomethingElse() }
```

---

## **8. What are Kotlin coroutines?**

**Coroutines:** Lightweight threads for asynchronous programming.

**Key Points:**

* Non-blocking
* Efficient memory usage
* Works with `suspend` functions

**Example:**

```kotlin
GlobalScope.launch {
    val data = fetchData()
    println(data)
}

suspend fun fetchData(): String {
    delay(1000)
    return "Hello Coroutine"
}
```

---

## **9. Difference between `map`, `flatMap`, and `filter` in Kotlin**

| Function  | Description                           | Example                                      |
| --------- | ------------------------------------- | -------------------------------------------- |
| `map`     | Transforms each element               | `[1,2,3].map { it * 2 }` → `[2,4,6]`         |
| `flatMap` | Maps + flattens nested lists          | `[[1,2],[3,4]].flatMap { it }` → `[1,2,3,4]` |
| `filter`  | Filters elements based on a condition | `[1,2,3,4].filter { it > 2 }` → `[3,4]`      |

---

## **10. Difference between `lateinit` and `lazy`**

| Keyword    | Description                                                                 |
| ---------- | --------------------------------------------------------------------------- |
| `lateinit` | For **var**, initialized later; cannot be used with nullable types or `val` |
| `lazy`     | For **val**, initialized lazily on first access                             |

**Example:**

```kotlin
lateinit var name: String
val age: Int by lazy { computeAge() }
```
