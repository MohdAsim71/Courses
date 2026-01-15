{
  "course": "Kotlin",
  "level": "Beginner",
  "category": "Interview Questions",
  "questions": [
    {
      "id": 1,
      "title": "What is Kotlin?",
      "difficulty": "Easy",
      "tags": ["basics", "introduction"],
      "askedIn": ["Google", "Amazon"],
      "markdown": "### ✅ What is Kotlin?\n\nKotlin is a **modern, statically typed programming language** developed by **JetBrains**.\n\n#### 🔹 Key Points:\n- Officially supported by **Google for Android development**\n- **100% interoperable with Java**\n- Concise and expressive syntax\n- Supports **object-oriented** and **functional programming**\n\n👉 Kotlin helps developers write **cleaner, safer, and shorter code** compared to Java."
    },
    {
      "id": 2,
      "title": "Why is Kotlin preferred over Java?",
      "difficulty": "Easy",
      "tags": ["basics", "java-interoperability"],
      "askedIn": ["Google", "Flipkart"],
      "markdown": "### ✅ Why is Kotlin preferred over Java?\n\nKotlin is preferred over Java because it solves many problems that developers face in Java.\n\n#### 🔹 Advantages:\n- **Null safety** → reduces `NullPointerException`\n- **Less boilerplate code**\n- **Data classes** reduce repetitive code\n- **Coroutines** simplify async programming\n- Extension functions improve readability\n\n👉 This makes Kotlin **more productive and safer** for Android development."
    },
    {
      "id": 3,
      "title": "What is null safety in Kotlin?",
      "difficulty": "Easy",
      "tags": ["null-safety", "basics"],
      "askedIn": ["Google", "Amazon"],
      "markdown": "### ✅ What is null safety in Kotlin?\n\nNull safety is a **feature in Kotlin that prevents NullPointerExceptions (NPEs)** at compile time.\n\n#### 🔹 Example:\n```kotlin\nvar name: String? = null\nprintln(name?.length)\n```\n\n#### 🔹 Operators:\n- `?` → Nullable type\n- `?.` → Safe call\n- `?:` → Elvis operator\n- `!!` → Not-null assertion (⚠️ risky)\n\n👉 Kotlin forces you to **handle null values explicitly**, making apps more stable."
    },
    {
      "id": 4,
      "title": "What is a data class?",
      "difficulty": "Easy",
      "tags": ["data-class", "basics"],
      "askedIn": ["Amazon", "Swiggy"],
      "markdown": "### ✅ What is a Data Class?\n\nA **data class** in Kotlin is used to hold data.\n\n#### 🔹 Benefits:\n- Automatically provides `toString()`\n- `equals()` and `hashCode()`\n- `copy()` function\n\n#### 🔹 Example:\n```kotlin\ndata class User(val name: String, val age: Int)\n```\n\n👉 Data classes help reduce **boilerplate code** significantly."
    },
    {
      "id": 5,
      "title": "What are Kotlin Coroutines?",
      "difficulty": "Easy",
      "tags": ["coroutines", "async"],
      "askedIn": ["Google", "Uber"],
      "markdown": "### ✅ What are Kotlin Coroutines?\n\nCoroutines are Kotlin’s solution for **asynchronous programming**.\n\n#### 🔹 Why Coroutines?\n- Lightweight\n- Easy to read and maintain\n- Avoid callback hell\n\n#### 🔹 Example:\n```kotlin\nlaunch {\n    val data = fetchData()\n    updateUI(data)\n}\n```\n\n👉 Coroutines make async code look **sequential and clean**."
    }
  ]
}
