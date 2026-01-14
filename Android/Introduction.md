# Introduction to Android Development

Welcome to the **Android Development course**! 🎉  
In this course, you will learn how to build modern, responsive, and professional Android apps using **Kotlin** and **Jetpack libraries**.

Android is the **most popular mobile platform**, and this course will guide you from **beginner concepts** to **advanced app development**.

---

## Why Learn Android Development?

Android development is:

- 🔹 **High in demand** – millions of apps on Google Play  
- 🔹 **Versatile** – apps for phones, tablets, TVs, and wearables  
- 🔹 **Flexible** – supports Java and Kotlin  
- 🔹 **Rich ecosystem** – Jetpack libraries, Compose, and Firebase  
- 🔹 **Career-friendly** – excellent for freelancers, startups, and product companies  

![Android Logo](assets/android_logo.png)

---

## What You Will Learn in This Course

- Basics: Activities, Fragments, Layouts  
- Views: TextView, Button, RecyclerView  
- Jetpack Compose: Declarative UI for modern apps  
- Navigation: Screen navigation and passing data  
- Data Storage: Room, SharedPreferences  
- Networking: Retrofit, APIs, JSON parsing  
- Firebase: Authentication, Realtime Database, Firestore  
- Advanced topics: Coroutines, StateFlow, MVVM architecture  
- Hands-on projects: Real-world Android apps  

---

## Hello World in Android

Let’s start with the classic **Hello World** app:

```kotlin
// MainActivity.kt
package com.example.helloworld

import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.compose.material3.Text
import androidx.compose.runtime.Composable

class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            HelloWorldScreen()
        }
    }
}

@Composable
fun HelloWorldScreen() {
    Text(text = "Hello, Android!")
}
