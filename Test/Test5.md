### What is Android?

Android is an **open-source operating system** developed by **Google**, built on top of the **Linux kernel**. It is mainly designed for **mobile devices**, but is also used across a wide range of smart devices.

### Where Android Is Used
Android powers multiple types of devices, including:
- **Smartphones and tablets**
- **Smart TVs** (Android TV)
- **Smartwatches** (Wear OS)
- **Cars** (Android Auto)
- **IoT and embedded devices** such as kiosks, POS systems, and smart displays

### Programming Languages Supported
Android supports application development using multiple programming languages:
- **Kotlin** – Officially recommended by Google, modern, concise, and safe
- **Java** – Original Android language with a large existing codebase
- **C++** – Used via the Android NDK for performance-critical tasks like games and media processing



### What is Context in Android?

In Android, **Context** is an abstract class that provides access to **application-specific resources and system services**. It allowing components to interact with resources like layouts, strings, databases, preferences, and system-level services.

### Context is commonly used to

- Access application **resources** (strings, colors, dimensions)
- Inflate **layouts** and create views
- Start **activities** and **services**
- Access **system services** (LocationManager, NotificationManager, etc.)
- Show **UI elements** like Toasts, Dialogs, and Snackbars
- Access **SharedPreferences**, files, and databases


### Types of Context in Android

Android provides **three main types of Context**, each used for different purposes.

### 1. Application Context
- `getApplicationContext()`
- Lives for the **entire app lifecycle**
- Used for **singletons, background work, and non-UI resources**

### 2. Activity Context
- Provided by an **Activity**
- Tied to the **Activity lifecycle**
- Used for **UI work** like dialogs and layout inflation

### 3. Service Context
- Provided by a **Service**
- Used for **background operations**
- Not suitable for UI


### Android Application Components

Android application components are the **core building blocks** of an app. Each component has a specific role and lifecycle managed by the Android system.

There are **four main Android application components**:

### 1. Activity
- Represents a **single UI screen**
- Handles user interaction
- Manages screen lifecycle


### 2. Service
- Performs **background tasks**
- Runs without a user interface
- Used for long-running operations


### 3. Broadcast Receiver
- Listens for **system or app events**
- Responds to events like battery change or network status
- Has no UI


### 4. Content Provider
- Manages and shares **app data**
- Supports CRUD operations
- Ensures secure data access between apps



### What is AndroidManifest.xml?

**AndroidManifest.xml** is a **mandatory configuration file** in every Android app. It provides essential information to the **Android system** before the app can be installed or launched.

### Why It Is Used
It tells Android:
- The app’s **package name**
- Which **components** the app has
- What **permissions** are required
- The app’s **launcher (entry point)**
- App-level settings and SDK support


### What It Contains
- **Application info** (name, icon, theme)
- **App components** (Activities, Services, Receivers, Providers)
- **Permissions**
- **Launcher Activity**
- **Min & target SDK versions**


### What is Application Class?

The **Application class** in Android is a **base class** that represents the **entire application**. It is created **before any Activity, Service, or other app component** and remains alive as long as the application process exists.

### Why It Is Used
The Application class is used to:
- Maintain **global application state**
- Initialize **app-wide libraries** (Firebase, analytics, DI, etc.)
- Store objects that need to live throughout the app lifecycle
- Access a **global context**

### Key Characteristics
- Only **one instance** exists per app
- Created **once** when the app starts
- Destroyed when the app process is killed
- Has the **longest lifecycle** in the app


### How It Is Used
Create a custom Application class and register it in the manifest.

```kotlin
class MyApp : Application() {
    override fun onCreate() {
        super.onCreate()
        // App-level initialization
    }
}
```



### What is ADB in Android?

**ADB (Android Debug Bridge)** is a **command-line tool** that allows developers to **communicate with an Android device or emulator** from a computer. It is mainly used for **debugging, testing, and managing** Android applications.

### Why It Is Used
ADB helps developers to:
- Install and uninstall apps
- Run shell commands on a device
- View logs and debug issues
- Transfer files between device and system
- Control devices during development

### Key Features
- Works with **real devices and emulators**
- Supports app debugging and testing
- Allows direct access to the device shell

### Common ADB Commands
- `adb devices` – List connected devices
- `adb install app.apk` – Install an app
- `adb logcat` – View device logs
- `adb shell` – Access device shell



### What is AAPT (Android Asset Packaging Tool)?

**AAPT (Android Asset Packaging Tool)** is a **build tool** used by Android to **compile, package, and manage app resources** such as layouts, images, and the AndroidManifest.xml file.

### Why It Is Used
AAPT is used to:
- Compile **resource files** (XML, images, strings)
- Generate the **R.java / R class** for resource access
- Package resources into the **APK or AAB**
- Validate resource references and manifest entries


### Key Responsibilities
- Converts resources into a **binary format**
- Links resources with application code
- Ensures resource IDs are correctly assigned



### What is a DEX File?

A **DEX (Dalvik Executable) file** is a compiled file format used by Android to store an app’s **bytecode**. It is generated from Java or Kotlin code and is executed by the **Android Runtime (ART)** on the device.

### Why It Is Used
DEX files are used to:
- Convert Java/Kotlin bytecode into a format optimized for Android
- Reduce memory usage on mobile devices
- Allow efficient execution on Android runtime

### Key Characteristics
- Contains all compiled classes of an app
- Optimized for low memory and performance
- Generated during the build process from `.class` files

---


### What is Multidex?

**Multidex** is an Android feature that allows an application to **use more than one DEX file**. It is required when an app exceeds the **65,536 method limit** imposed on a single DEX file.

### Why Multidex Is Needed
Apps with many libraries (Firebase, Retrofit, Google Play Services, etc.) can cross the **65K method limit**. Multidex splits code into **multiple DEX files** so the app can build and run correctly.


### Example Configuration

#### Enable Multidex
```gradle
android {
    defaultConfig {
        multiDexEnabled true
    }
}

dependencies {
    implementation "androidx.multidex:multidex:2.0.1"
}
```


### What are Processes in Android?

A **process** is a running instance of an app with its **own memory space**. Android runs each app in a **separate Linux process** to ensure security and stability.

### Why Processes Are Used
- Keeps apps **isolated and secure**
- Manages **memory and performance**
- Prevents one app crash from affecting others

### Process Priority Types
- **Foreground** – App in use (highest priority)
- **Visible** – Partially visible app
- **Service** – Background work (e.g., music)
- **Background** – Not visible
- **Empty** – No active components (lowest priority)



### Can an Android App Run in Multiple Processes?

**Yes**, an Android application **can run in multiple processes**.

By default, all components of an app run in a **single process**, but Android allows you to assign **different components to different processes** using the `android:process` attribute.

---

### How to Run an App in Multiple Processes

You can specify a custom process name in **AndroidManifest.xml** for a component.

```xml
<service
    android:name=".MyService"
    android:process=":background" />
````

### How It Works

* The `:background` prefix creates a **private process** for the app
* That component runs in a **separate process**
* The rest of the app continues to run in the main process

---

### Use Cases

* Heavy background work
* Isolating crash-prone components
* Improving performance for specific tasks


## How is Memory Managed in Android OS?

Android manages memory automatically to ensure smooth performance and efficient use of system resources.

### Key Points:

- **Linux-based Memory Management**  
  Android runs on the Linux kernel, which handles low-level memory operations like paging and allocation.

- **Garbage Collection (GC)**  
  Android apps run on ART (Android Runtime), which automatically frees unused objects using garbage collection, so developers don’t manually manage memory.

- **Process Priority & Lifecycle**  
  Android assigns priority to apps based on their state:
    - Foreground app (highest priority)
    - Visible app
    - Background app
    - Cached app (lowest priority)

- **Low Memory Killer (LMK)**  
  When memory is low, Android kills low-priority background processes to free memory.

- **Shared Resources**  
  System resources like libraries are shared across apps to reduce memory usage.

- **Developer Responsibility**  
  Developers should:
    - Avoid memory leaks
    - Release resources (bitmaps, listeners)
    - Use lifecycle-aware components



### What is StrictMode in Android?

**StrictMode** is a **debugging tool** that helps detect **performance issues** like disk/network calls on the main thread and **memory leaks**.

### Purpose
- Catch bad coding practices  
- Prevent ANRs  
- Improve app responsiveness  

### How It Works
- **Thread Policy:** Monitors main-thread operations  
- **VM Policy:** Detects memory leaks  

### Key Points
- Used only in **development**
- Not recommended for **production**



### What is Lint in Android?

**Lint** is a **static code analysis tool** in Android that helps developers **identify and fix potential bugs, performance issues, and code quality problems** in their apps before runtime.

### Why It Is Used
- Detect **common coding mistakes**
- Identify **performance and usability issues**
- Enforce **best practices and standards**
- Prevent **runtime crashes**

### How It Works
- Scans **Java, Kotlin, XML, and Gradle files**
- Provides **warnings or errors** for:
    - Unused resources
    - Hardcoded text (i18n issues)
    - Missing permissions
    - Deprecated APIs
    - Layout performance issues

### Key Points
- Runs **at compile-time**
- Integrated in **Android Studio**
- Helps maintain **clean and efficient code**

### What is Support Library in Android?

The **Android Support Library** is a set of **code libraries** provided by Google to help developers **use newer Android features on older versions** of the platform. It provides **backward-compatible versions of APIs**, UI components, and utilities.

---

### Why It Was Introduced
- **Fragmented Android versions:** Not all devices run the latest Android OS.
- **Backward compatibility:** Allows developers to use modern features on older devices.
- **Consistent UI and functionality:** Ensures apps behave similarly across different Android versions.
- **Faster development:** Provides ready-to-use components like RecyclerView, CardView, ViewPager, etc.

---

### Key Features
- Backward-compatible UI widgets (RecyclerView, CardView, Toolbar)
- Support for newer APIs on older devices
- Utility classes for tasks like notifications, media, and animations

---

### Doze Mode & App Standby in Android

Both **Doze Mode** and **App Standby** help **save battery** by limiting background work.

### Doze Mode
- Activates when device is **idle, screen off**
- Delays background tasks, syncs, and network
- Allows **high-priority notifications**

### App Standby
- Applies to **unused apps**
- Restricts background jobs and network
- Active apps are not affected

### In Short
- **Doze Mode:** Affects the whole device  
- **App Standby:** Affects unused apps only



### File, Class, and Activity in Android

### File
- Used to **store data** on the device (internal, external, cache)
- Examples: text files, images, databases

### Class
- A **blueprint** written in Kotlin/Java
- Defines variables and functions
- All Android components are classes

### Activity
- Represents **one screen with UI**
- Handles user interaction
- Managed by the Android lifecycle



### How to Change Parameters in an App Without App Update

### Changing App Parameters Without App Update

You can update app behavior **without releasing a new version** using **remote configuration**.

### Common Ways
- **Firebase Remote Config:** Fetch key-value updates at runtime (UI text, feature flags)
- **Backend API:** Load configurable values from your server
- **Dynamic Feature Modules:** Enable or disable app features remotely

### Benefits
- No app update required
- Easy feature toggles & A/B testing
- Quick content or behavior changes



### What is an Activity and Its Lifecycle in Android

An **Activity** is a single screen in Android that handles user interaction and displays the UI.

### Activity Lifecycle

- **onCreate()** – Initialize UI and resources when Activity is first created.  
- **onStart()** – Activity becomes visible.  
- **onResume()** – Activity gains focus; user can interact.  
- **onPause()** – Activity loses focus; pause tasks or save data.  
- **onStop()** – Activity no longer visible; release resources.  
- **onDestroy()** – Activity is destroyed; cleanup resources.  
- **onRestart()** – Activity restarts after being stopped.



### Key Points
- Manages **visibility, focus, and resources**.  
- Prevents **crashes and data loss**.  
- Lifecycle methods guide proper handling of UI and background tasks.


### Difference Between onCreate() and onStart() in Android

- **When Called:**
    - `onCreate()` is called **once** when the Activity is first created.
    - `onStart()` is called **every time** the Activity becomes visible.
---

- **Purpose:**
    - `onCreate()` is used to **initialize UI, resources, and data**.
    - `onStart()` prepares the Activity to **interact with the user**.
---

- **Typical Tasks:**
    - `onCreate()` → set content view, bind views, initialize variables.
    - `onStart()` → start animations, refresh UI, resume paused tasks.
---

- **Lifecycle Position:**
    - `onCreate()` is the **first method** called in the Activity lifecycle.
    - `onStart()` follows `onCreate()` or `onRestart()`.



### When is onDestroy() Called Without onPause() and onStop()?

Normally, `onPause()` and `onStop()` run before `onDestroy()`, but they can be skipped in rare cases:

- **Activity finishes early** (e.g., `finish()` during `onCreate()`)
- **System kills the process** due to low memory
- **App crash or fatal exception**

### Key Point
- `onDestroy()` is **not always guaranteed**
- Do important cleanup in `onPause()` or `onStop()`, not `onDestroy()`


### Activity Lifecycle When Launched for the First Time

When an Android Activity is launched for the **first time**, it goes through the following lifecycle methods in order:

1. **onCreate()**  
   - Called when the Activity is **first created**.  
   - Used to **initialize UI, variables, and resources**.  
   - Example: `setContentView(R.layout.activity_main)`
   - 

2. **onStart()**  
   - Called when the Activity **becomes visible** to the user.  
   - Prepares the Activity to **enter the foreground**.

3. **onResume()**  
   - Called when the Activity **gains focus** and the user can interact with it.  
   - Activity is now in the **foreground** and fully active.

---

### Lifecycle Flow for First Launch


onCreate → onStart → onResume
### Key Points
- The Activity is **fully created and visible** after `onResume()`.  
- `onPause()` and `onStop()` are called only when the user **leaves or navigates away** from the Activity.  


### Activity Lifecycle When Back Button Is Pressed

When the user **presses the Back button**, the current Activity is **finished** and removed from the screen. The system calls the following lifecycle methods in order:

1. **onPause()**  
   - Called first when the Activity **loses focus**.  
   - Used to pause ongoing tasks, animations, or save unsaved data.

2. **onStop()**  
   - Called when the Activity is **no longer visible**.  
   - Release resources that are not needed while the Activity is hidden.

3. **onDestroy()**  
   - Called when the Activity is **completely destroyed**.  
   - Final cleanup of resources occurs here.

---

### Lifecycle Flow When Back Pressed
onPause → onStop → onDestroy

### Key Points
- Pressing Back **finishes the Activity**, unlike Home button which only pauses/stops it.  
- After `onDestroy()`, the Activity **cannot be resumed**.


### Activity Lifecycle When Launched Again After Back Press

When an Activity is **launched again after being finished with the Back button**, it is treated as a **new instance**. The previous instance was destroyed, so the lifecycle starts fresh:

1. **onCreate()**  
   - Called to **create a new Activity instance**.  
   - Initialize UI, variables, and resources.

2. **onStart()**  
   - Called when the Activity **becomes visible** to the user.

3. **onResume()**  
   - Called when the Activity **gains focus** and the user can interact with it.  
   - The Activity is now in the **foreground**.

---

### Lifecycle Flow

onCreate → onStart → onResume

### Key Points
- Pressing Back **destroys the Activity**, so launching it again starts a **fresh lifecycle**.  
- Any previous state must be **saved manually** (e.g., using `SharedPreferences` or a database) if needed.


### Activity Lifecycle When Home Button Is Pressed

When the user **presses the Home button**, the current Activity **moves to the background** but is **not destroyed**. The system calls the following lifecycle methods:

1. **onPause()**  
   - Called first as the Activity **loses focus**.  
   - Use to **pause animations, save data, or stop CPU-intensive tasks**.

2. **onStop()**  
   - Called when the Activity is **no longer visible**.  
   - Release resources that are not needed while in the background.

> Note: The Activity **remains in memory** and can be resumed later without being recreated.

### Lifecycle Flow When Home Pressed

onPause → onStop

### Key Points
- Activity is **paused and stopped**, but not destroyed.  
- Pressing **Back button** would have destroyed it, unlike Home button.  
- When the user returns, `onRestart()` → `onStart()` → `onResume()` is called.



### Activity Lifecycle When App Returns from Background

When an Android app **returns from the background** (e.g., user presses the app icon or switches back from recent apps), the previously stopped Activity is **resumed** without being recreated. The following lifecycle methods are called:

1. **onRestart()**  
   - Called first when the Activity is **coming back from stopped state**.  
   - Prepares the Activity to become visible again.

2. **onStart()**  
   - Called as the Activity **becomes visible** to the user.

3. **onResume()**  
   - Called when the Activity **gains focus** and the user can interact with it.  
   - Activity is now in the **foreground**.

---

### Lifecycle Flow

onRestart → onStart → onResume

### Key Points
- Activity **was not destroyed**, so `onCreate()` is **not called**.  
- Efficient memory and resource usage, since UI and data are retained.  
- Use `onRestart()` or `onStart()` to **refresh UI or data** if needed.


### Activity Lifecycle When Navigating from Activity A → Activity B

When the user navigates from **Activity A** to **Activity B**, the system manages the lifecycle of both Activities to ensure smooth transitions and resource management.

### Activity Lifecycle: A → B

**Activity A**
- `onPause()` → loses focus
- `onStop()` → no longer visible

**Activity B**
- `onCreate()` → created
- `onStart()` → visible
- `onResume()` → interactive

**Flow**
A: `onPause → onStop`  
B: `onCreate → onStart → onResume`

**Note**
- Activity A stays in memory
- Pressing Back destroys B and resumes A


### Activity Lifecycle When Pressing Back from Activity B → Activity A

When the user presses the **Back button** on **Activity B**, it is **finished**, and the system returns to **Activity A**. The lifecycle methods of both Activities are called as follows:


**Activity B**
- `onPause()` → loses focus  
- `onStop()` → not visible  
- `onDestroy()` → finished  

**Activity A**
- `onRestart()` → coming back  
- `onStart()` → visible  
- `onResume()` → interactive  

**Flow**
B: `onPause → onStop → onDestroy`  
A: `onRestart → onStart → onResume`



### How to Preserve Activity State During Screen Rotation

When an Activity is rotated, it is **destroyed and recreated**. To preserve state:


### Common Ways
- **onSaveInstanceState():** Save small UI data (text, selections)
- **ViewModel:** Keeps UI data across rotations

### Key Points
- `onSaveInstanceState()` → temporary UI state  
- `ViewModel` → long-lived UI data  
- Avoid manual config handling unless necessary



### What is `savedInstanceState`?

`savedInstanceState` is a **Bundle** used to **save and restore UI state** when an Activity is recreated (e.g., screen rotation).

### How It’s Used
- Save data in `onSaveInstanceState()`
- Restore it in `onCreate()` or `onRestoreInstanceState()`

### Key Points
- `null` on first launch
- Stores **small UI data only**
- Helps restore state after rotation or system kill


### Intent vs Bundle

**Intent**
- Used to **start Activities/Services** or send broadcasts
- Can carry data and navigation info

**Bundle**
- A **key-value data container**
- Used to pass data via Intent or save state

**In Short**
- **Intent** = navigation + data
- **Bundle** = data only


### What Are Launch Modes in Android?

**Launch modes** define **how a new Activity is launched** and how it behaves in the **Activity back stack**. They control whether a new instance is created or an existing instance is reused.
### Types of Launch Modes

1. **standard** (Default)  
   - Every time the Activity is started, a **new instance** is created and pushed to the stack.  
   - Example: Multiple instances of the same Activity can exist.

2. **singleTop**  
   - If the Activity is **already at the top** of the stack, no new instance is created.  
   - `onNewIntent()` is called instead.  
   - Example: Clicking a notification that opens the current top Activity.

3. **singleTask**  
   - Only **one instance** exists in the entire system.  
   - If an instance exists anywhere in the stack, it is **brought to the front**, and `onNewIntent()` is called.  
   - Example: Main dashboard Activity.

4. **singleInstance**  
   - Similar to `singleTask` but the Activity **lives in its own separate task**.  
   - No other Activity can be part of the same task.  
   - Example: Launching a special Activity for multi-window scenarios.

---

### How to Declare Launch Mode
In `AndroidManifest.xml`:
```xml
<activity android:name=".MainActivity"
          android:launchMode="singleTop" />
````

---

### Key Points

* Launch modes **control Activity instance creation** and **stack behavior**.
* Helps prevent **duplicate Activities** and manage navigation efficiently.

---


### Standard Launch Mode in Android

**standard** is the **default launch mode** for all Activities in Android.  

---

### How It Works
- Every time the Activity is started, a **new instance** is **created and pushed onto the back stack**.  
- Multiple instances of the same Activity can exist simultaneously in the back stack.  
- Does **not reuse any existing instance**.

---

### Example
```kotlin
// Start MainActivity multiple times
val intent = Intent(this, MainActivity::class.java)
startActivity(intent)
startActivity(intent)
````

* Result: Two separate instances of `MainActivity` are now in the back stack.

---

### Key Points

* Allows **multiple instances** of the same Activity.
* Each instance is independent.
* Useful when each Activity should maintain its **own state**.


### singleTop Launch Mode in Android

**singleTop** is a launch mode that **reuses the Activity** if it is **already at the top of the back stack**, instead of creating a new instance.

---

### How It Works
- If the Activity is **not at the top**, a new instance is created (like standard mode).  
- If the Activity **is at the top**, no new instance is created; **`onNewIntent()`** is called with the new Intent.  
- Prevents multiple copies of the same Activity when repeatedly launching it from the top.

---

### Example
```kotlin
// Activity A is at the top of the stack
val intent = Intent(this, ActivityA::class.java)
startActivity(intent) // onNewIntent() is called instead of creating a new instance
````

---

### Key Points

* Avoids **duplicate instances** at the top of the stack.
* Saves **memory and resources**.
* Useful for **notification clicks** or launching an Activity multiple times from the same screen.

### singleTask Launch Mode in Android

**singleTask** is a launch mode that ensures **only one instance of an Activity exists** in the system, and it is **reused if it already exists** anywhere in the back stack.

---

### How It Works
- If the Activity **already exists** in the back stack:
  - The system brings that instance to the **foreground**.
  - **All Activities above it** in the stack are **destroyed**.
  - `onNewIntent()` is called with the new Intent.
- If the Activity **does not exist**, a new instance is created.

---

### Example
```kotlin
// MainActivity is launched with singleTask
val intent = Intent(this, MainActivity::class.java)
startActivity(intent)
````

* If MainActivity exists anywhere in the stack, it is **reused**, and other Activities above it are removed.

---

### Key Points

* Ensures **only one instance** of the Activity exists system-wide.
* Useful for **main dashboard or launcher Activities**.
* Helps manage navigation and prevent duplicate screens.



### singleInstance Launch Mode in Android

**singleInstance** is a special launch mode that ensures **only one instance of an Activity exists**, and it **resides in its own separate task**. No other Activity can be launched in the same task.


#### How It Works
- The Activity runs in a **separate task**, isolated from other Activities.  
- If the Activity already exists:
  - It is **reused**, and `onNewIntent()` is called.  
  - No other Activities can be part of its task.  
- Useful for **Activities that must always be standalone**, like a special media player or system-level screen.

---

#### Example
```xml
<activity
    android:name=".SpecialActivity"
    android:launchMode="singleInstance" />
````

* Launching SpecialActivity multiple times **reuses the same instance** in its separate task.

---

### Key Points

* Guarantees **one instance in a separate task**.
* Prevents **other Activities** from being launched in the same task.
* Ideal for **system-level or always-on-top Activities**.


### Tasks and Back Stack in Android

In Android, **tasks** and the **back stack** are concepts that define how Activities are organized and navigated.

---

### 1. Task
- A **task** is a collection of Activities that users interact with **to accomplish a specific goal**.  
- Activities in a task are **organized in a stack-like structure**.  
- Each app usually has its **own task**, but tasks can span multiple apps with certain launch modes.  
- Example: Opening an email app, reading an email, then composing a new one—all belong to the same task.

---

### 2. Back Stack
- The **back stack** is a **Last-In-First-Out (LIFO) stack** that manages the order of Activities within a task.  
- The **top of the stack** is the **current Activity** in the foreground.  
- Pressing the **Back button** pops the top Activity off the stack and resumes the previous one.

---

### Example
1. User opens **Activity A** → pushed onto stack  
2. Navigates to **Activity B** → pushed onto stack  
3. Presses Back → **Activity B** popped, **Activity A** resumes  

```
Stack after opening B: [A, B]  (B on top)
Press Back: [A]  (B removed)
```


### Key Points
- **Task** = logical group of related Activities.  
- **Back stack** = manages Activity order in a task.  
- **Back button** navigates through the back stack, not tasks. 


### What is `taskAffinity` in Android

**`taskAffinity`** is an attribute of an Activity that defines **which task the Activity prefers to belong to**. It allows Activities from the same or different apps to be associated with a particular task.

---

### How It Works
- By default, all Activities of an app share the **same taskAffinity** (usually the app package name).  
- You can set a **custom taskAffinity** in `AndroidManifest.xml` to control task behavior.  
- When launching an Activity, the system tries to place it in a task with the **same taskAffinity**.

---

### Example
```xml
<activity
    android:name=".SpecialActivity"
    android:taskAffinity="com.example.specialtask" />
````

* `SpecialActivity` will prefer to run in a task named `com.example.specialtask`.
* Useful for creating **separate tasks for specific Activities** (e.g., for multi-window apps or notifications).

---

### Key Points

* Controls **task association** for Activities.
* Helps **manage multiple tasks** within the same app.
* Does **not force** the system to create a new task; it’s a **preference**.


### What is `installLocation` Tag in Android

The **`installLocation`** tag in `AndroidManifest.xml` specifies **where the app should be installed** on the device. It helps control whether the app installs on **internal storage** or **external storage (SD card)**.

---

### Possible Values

1. **internalOnly** (Default)  
   - App can only be installed on **internal storage**.  
   - Ensures the app is always available and not removable by the user.

2. **preferExternal**  
   - App **prefers external storage** (SD card), but can fall back to internal storage if needed.  
   - Useful for large apps to save internal memory.

3. **auto**  
   - The system decides the **best location** based on available space and device configuration.

---

### Example
```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.app">
    
    <application
        android:installLocation="preferExternal"
        android:label="@string/app_name">
    </application>
</manifest>
````

---

### Key Points

* Helps manage **storage usage** for large apps.
* Some features may **not work on SD card** (e.g., widgets, services).
* Default is **internalOnly** if not specified.


### Relationship Between Activity and Fragment Lifecycle

- Fragments exist **inside an Activity**, so their lifecycle is **closely tied** to the host Activity.  
- Fragment lifecycle events occur **alongside the Activity**, but Fragments have **extra callbacks** like `onAttach()`, `onCreateView()`, and `onDetach()` for managing UI.

**Lifecycle Mapping (Simplified):**
- Activity `onCreate()` → Fragment `onAttach()` → `onCreateView()`  
- Activity `onStart()` → Fragment `onStart()`  
- Activity `onResume()` → Fragment `onResume()`  
- Activity `onPause()` → Fragment `onPause()`  
- Activity `onStop()` → Fragment `onStop()`  
- Activity `onDestroy()` → Fragment `onDestroyView()` → `onDestroy()` → `onDetach()`

**Key Points:**  
- Fragment depends on Activity but can manage its own UI.  
- Proper lifecycle handling prevents **memory leaks** and ensures **smooth UI updates**.

### Saving and Restoring Activity State on Rotation

When an Activity rotates, it is **destroyed and recreated**. To preserve state:

---

### 1. `onSaveInstanceState()`
```kotlin
override fun onSaveInstanceState(outState: Bundle) {
    super.onSaveInstanceState(outState)
    outState.putString("username", editText.text.toString())
}

override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    editText.setText(savedInstanceState?.getString("username"))
}
````

---

### 2. ViewModel

* Survives rotation without recreation.

```kotlin
val viewModel = ViewModelProvider(this).get(MyViewModel::class.java)
editText.setText(viewModel.username)
viewModel.username = editText.text.toString()
```

### What is a Bundle in Android

In Android, a **Bundle** is a **key-value data container** used to pass information between components like Activities, Fragments, or Services.

---

### Key Points
- Stores data as **primitive types, Strings, Parcelable, or Serializable objects**.  
- Often used with:
  - **Intents** to pass data between Activities.
  - **Fragments** via `setArguments()` or `getArguments()`.
  - **onSaveInstanceState()`** to save Activity state.

---

### Example with Intent
```kotlin
val bundle = Bundle()
bundle.putString("username", "Aasim")

val intent = Intent(this, SecondActivity::class.java)
intent.putExtras(bundle)
startActivity(intent)
````

### Example in Fragment

```kotlin
val fragment = MyFragment()
val bundle = Bundle()
bundle.putInt("userId", 101)
fragment.arguments = bundle
```


### Lifecycle Order When Activity A Starts Activity B

When **Activity A** starts **Activity B**, both Activities go through specific lifecycle callbacks as the system manages focus and visibility.

---

### Activity A (Current Activity)
1. **onPause()** – Activity A **loses focus** because Activity B is coming to the foreground.  
2. **onStop()** – Called if Activity B **fully covers Activity A**. Activity A is now **in the background**.

---

### Activity B (New Activity)
1. **onCreate()** – Activity B is **created** and UI is initialized.  
2. **onStart()** – Activity B becomes **visible**.  
3. **onResume()** – Activity B **gains focus** and user can interact with it.



### Lifecycle Flow (Simplified)

```
Activity A: onPause → onStop
Activity B: onCreate → onStart → onResume
```

### Key Points
- Activity A is **paused or stopped** but not destroyed.  
- Activity B starts fresh and becomes the **foreground Activity**.  
- Pressing **Back** from Activity B will **resume Activity A** using `onRestart() → onStart() → onResume()`.


### How to Declare Launch Mode in Android

In Android, you can declare an Activity's **launch mode** in the **`AndroidManifest.xml`** file using the `android:launchMode` attribute.

---

### Steps to Declare Launch Mode

1. Open `AndroidManifest.xml`.  
2. Inside the `<activity>` tag, add `android:launchMode` with one of the following values:  
   - `standard` (default)  
   - `singleTop`  
   - `singleTask`  
   - `singleInstance`

---

### Example
```xml
<activity
    android:name=".MainActivity"
    android:launchMode="singleTop" />
````

* This ensures that if `MainActivity` is already at the **top of the stack**, no new instance is created; `onNewIntent()` is called instead.

---

### Key Points

* Launch mode controls **Activity instance creation** and **back stack behavior**.
* Declaring it in the manifest applies **system-wide** for that Activity.
* Useful for preventing **duplicate screens** and managing **navigation flow**.



### Detecting Configuration Changes in `onDestroy()`

In Android, an Activity may be **destroyed either due to user action or a configuration change** (like screen rotation). To differentiate in `onDestroy()`, use `isChangingConfigurations()`.

---

### How It Works
- `isChangingConfigurations()` returns **true** if the Activity is being destroyed due to a **configuration change**.  
- Returns **false** if destroyed for other reasons (e.g., user finishing the Activity or system reclaiming memory).

---

### Example
```kotlin
override fun onDestroy() {
    super.onDestroy()
    if (isChangingConfigurations) {
        Log.d("ActivityLifecycle", "Destroyed due to configuration change")
    } else {
        Log.d("ActivityLifecycle", "Destroyed permanently")
    }
}
````

---

### Key Points

* Helps decide whether to **save resources** or **release them permanently**.
* Often used with **ViewModel** to retain data across configuration changes.
* Works reliably with screen rotation, locale changes, or theme changes.



### What is a Fragment in Android

A **Fragment** is a **modular portion of an Activity** that has its own **lifecycle, UI, and behavior**. Fragments allow developers to create **reusable and flexible UI components** that can be combined in different ways within an Activity.

---

### Key Features
- Represents a **part of a screen**, not a full screen.  
- Can be **added, removed, or replaced dynamically** using `FragmentManager`.  
- Has its **own lifecycle**, which is closely tied to the host Activity.  
- Supports **UI layouts**, user interactions, and logic independent of the Activity.

---

### Example
```kotlin
class MyFragment : Fragment() {
    override fun onCreateView(
        inflater: LayoutInflater,
        container: ViewGroup?,
        savedInstanceState: Bundle?
    ): View? {
        return inflater.inflate(R.layout.fragment_my, container, false)
    }
}
````

* Add to Activity:

```kotlin
supportFragmentManager.beginTransaction()
    .replace(R.id.container, MyFragment())
    .commit()
```

---

### Key Points

* Fragments are **reusable UI components**.
* Allow **flexible layouts** for phones, tablets, and multi-pane screens.
* Lifecycle depends on the **host Activity** but has **independent callbacks**.

---



### Fragment Lifecycle Methods in Android

A **Fragment** has its **own lifecycle** that is closely tied to the host Activity. Understanding these methods helps manage UI and resources efficiently.

---

### Key Lifecycle Methods

1. **onAttach(Context)**  
   - Called when the Fragment is **attached to its host Activity**.  
   - Use for **context-related initializations**.

2. **onCreate(Bundle?)**  
   - Called to **initialize Fragment** (non-UI tasks).  
   - Use for **data setup**.

3. **onCreateView(LayoutInflater, ViewGroup?, Bundle?)**  
   - Inflate the Fragment **UI layout**.  

4. **onViewCreated(View, Bundle?)**  
   - Called after the **view hierarchy is created**.  
   - Use for **binding views and setting listeners**.

5. **onStart()**  
   - Fragment becomes **visible**.  

6. **onResume()**  
   - Fragment **gains focus** and is interactive.

7. **onPause()**  
   - Fragment **loses focus** but is still visible.  
   - Use to **pause UI updates or animations**.

8. **onStop()**  
   - Fragment is **no longer visible**.  
   - Release resources not needed when hidden.

9. **onDestroyView()**  
   - Fragment’s **view hierarchy is destroyed**.  
   - Clean up **binding references**.

10. **onDestroy()**  
    - Called to **cleanup Fragment instance**.  

11. **onDetach()**  
    - Fragment is **detached from Activity**.  
    - Final cleanup of references to Activity.


### Why Use Only the Default Constructor in a Fragment

In Android, it is **recommended to use only the default (no-argument) constructor** for Fragments. This ensures the system can **recreate the Fragment properly** during configuration changes or process recreation.

---

### Reasons

1. **System Recreation**
   - Android may **destroy and recreate Fragments** (e.g., on rotation or low memory).  
   - The system uses the **default constructor** to re-instantiate the Fragment.  
   - Custom constructors with arguments **will not be called**, causing crashes or lost data.

2. **Safe Data Passing**
   - Data should be passed using a **Bundle via `setArguments()`** instead of constructor parameters.  
   - `setArguments()` is preserved across **configuration changes**.

---

### Recommended Approach
```kotlin
class MyFragment : Fragment() {
    companion object {
        fun newInstance(userId: Int): MyFragment {
            val fragment = MyFragment()
            val args = Bundle()
            args.putInt("userId", userId)
            fragment.arguments = args
            return fragment
        }
    }
}
````

* Access data in Fragment:

```kotlin
val userId = arguments?.getInt("userId")
```

---

### Key Points

* Always use the **default constructor**.
* Use `setArguments()` / `Bundle` to pass data.
* Ensures **reliable Fragment recreation** by the system.




### Fragment Lifecycle When Launched

When a **Fragment is added to an Activity**, it goes through a series of **lifecycle callbacks** as it becomes visible and interactive.

---

### Lifecycle Sequence

1. **onAttach(Context)**  
   - Fragment is **attached to its host Activity**.  
   - Can access the Activity context.

2. **onCreate(Bundle?)**  
   - Fragment **initializes non-UI components** and data.  

3. **onCreateView(LayoutInflater, ViewGroup?, Bundle?)**  
   - Fragment **inflates its UI layout**.  

4. **onViewCreated(View, Bundle?)**  
   - UI is created; **views can be initialized and listeners set**.

5. **onStart()**  
   - Fragment becomes **visible** to the user.

6. **onResume()**  
   - Fragment is now **active and interactive**.

---

### Simplified Flow Diagram

onAttach → onCreate → onCreateView → onViewCreated → onStart → onResume

### Key Points
- Lifecycle is **closely tied to the host Activity**.  
- Proper handling ensures **UI is ready** and resources are efficiently managed.  
- After `onResume()`, the Fragment can **interact with the user**.



### Fragment Lifecycle When Back Button Is Pressed

When the **Back button** is pressed and a Fragment is removed or replaced, it goes through the **destruction phase** of its lifecycle.

---

### Lifecycle Sequence

1. **onPause()**  
   - Fragment **loses focus** and stops interacting with the user.  

2. **onStop()**  
   - Fragment is **no longer visible**.  

3. **onDestroyView()**  
   - Fragment’s **view hierarchy is destroyed**.  
   - Release UI-related resources here.

4. **onDestroy()**  
   - Fragment instance is **destroyed**, cleaning up non-UI resources.

5. **onDetach()**  
   - Fragment is **detached from its host Activity**.  
   - Final cleanup and references to Activity are cleared.

---

### Simplified Flow Diagram

onPause → onStop → onDestroyView → onDestroy → onDetach

### Key Points
- Back press triggers **removal of the Fragment’s UI and instance**.  
- Proper handling prevents **memory leaks**.  
- Any data that needs to persist should be saved in **ViewModel or savedInstanceState**.












































































