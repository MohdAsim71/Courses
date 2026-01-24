

---

## 1️⃣ What is Android?

Android is an **open-source mobile operating system** developed by Google, based on the Linux kernel.  
It is used to build applications for smartphones, tablets, TVs, wearables, and IoT devices.

### Key Features
- Open-source and customizable
- Supports Java, Kotlin, and C++
- Component-based architecture
- Large app ecosystem (Google Play)

---

## 2️⃣ What is Context? How is it used?

`Context` represents the environment in which an app is running.  
It provides access to app resources, system services, and application-level operations.

### Uses of Context
- Access resources (strings, colors, layouts)
- Start Activities and Services
- Show Toasts and Dialogs
- Access system services

### Example
```kotlin
Toast.makeText(this, "Hello Android", Toast.LENGTH_SHORT).show()
````

---

## 3️⃣ What is Application Context?

Application Context is tied to the **lifecycle of the entire application**.

### Characteristics

* Exists as long as the app is running
* Not tied to any UI component
* Used for long-lived operations

### Example

```kotlin
val context = applicationContext
```

---

## 4️⃣ What is Activity Context?

Activity Context is tied to the **lifecycle of an Activity**.

### Characteristics

* Exists only while the Activity is alive
* Used for UI-related operations

### Example

```kotlin
val context = this // inside Activity
```

---

## 5️⃣ Tell all Android application components.

Android has four main application components:

### 🔹 Activity

* Represents a UI screen
* Handles user interaction

### 🔹 Service

* Performs background tasks
* No UI

### 🔹 Broadcast Receiver

* Responds to system-wide events
* Example: network change, battery low

### 🔹 Content Provider

* Manages and shares app data
* Example: Contacts provider

---

## 6️⃣ What is AndroidManifest.xml?

`AndroidManifest.xml` is the configuration file of an Android app.

### It defines:

* App components (Activities, Services, Receivers)
* Permissions
* App entry point
* Package name
* SDK versions

### Example

```xml
<manifest package="com.example.app">

    <uses-permission android:name="android.permission.INTERNET"/>

    <application>
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN"/>
                <category android:name="android.intent.category.LAUNCHER"/>
            </intent-filter>
        </activity>
    </application>

</manifest>
```

---

## 7️⃣ What is Application class?

The `Application` class represents the **global state of the app**.
It is created before any Activity or Service.

### Use Cases

* Initialize libraries (Firebase, DI, Analytics)
* Store global data

### Example

```kotlin
class MyApp : Application() {
    override fun onCreate() {
        super.onCreate()
    }
}
```

---

## 8️⃣ What is ADB in Android?

ADB (Android Debug Bridge) is a command-line tool used to communicate with Android devices.

### Uses

* Install/uninstall apps
* Debug apps
* Execute shell commands

### Example

```bash
adb install app.apk
```

---

## 9️⃣ What is AAPT (Android Asset Packaging Tool)?

AAPT is a build tool that compiles and packages Android app resources.

### Responsibilities

* Compile XML resources
* Generate R.java / R.class
* Package APK or AAB

---

## 🔟 What is DEX file?

DEX (Dalvik Executable) file contains compiled bytecode of Android apps.
Java/Kotlin code is converted into DEX format for execution by Android Runtime (ART).

---

## 1️⃣1️⃣ What is Multidex?

Multidex allows an app to contain multiple DEX files when method count exceeds 65,536.

### Why needed?

Large apps exceed the single DEX limit.

### Example

```gradle
multiDexEnabled true
```

---

## 1️⃣2️⃣ What are processes in Android?

A process is an instance of a running application.
Android assigns priority to processes based on their importance.

### Process Priority Order

1. Foreground process
2. Visible process
3. Service process
4. Background process
5. Empty process

---

## 1️⃣3️⃣ Is it possible to run an Android app in multiple processes? How?

Yes ✅

### How?

By specifying `android:process` in `AndroidManifest.xml`.

```xml
<activity
    android:name=".MainActivity"
    android:process=":remote" />
```

### Use Cases

* Isolate heavy tasks
* Improve stability
* IPC (Inter-Process Communication)

---

## 1️⃣4️⃣ How is memory managed in Android OS?

Android uses automatic memory management through **Garbage Collection (GC)**.

### Memory Management Features

* Heap memory allocation
* Garbage Collector
* Low Memory Killer (LMK)
* Process termination when memory is low

### Best Practices

* Avoid memory leaks
* Use ViewBinding instead of findViewById
* Release resources in lifecycle methods

---

## 1️⃣5️⃣ What is StrictMode?

StrictMode is a developer tool used to detect bad practices in Android apps.

### Detects

* Disk I/O on main thread
* Network calls on main thread
* Memory leaks

### Example

```kotlin
StrictMode.setThreadPolicy(
    StrictMode.ThreadPolicy.Builder().detectAll().penaltyLog().build()
)
```

---

## 1️⃣6️⃣ What is Lint?

Lint is a static code analysis tool that checks Android code for bugs, performance issues, and best practices.

### Detects

* Unused resources
* Performance issues
* Security vulnerabilities

---

## 1️⃣7️⃣ What is Support Library? Why was it introduced?

The Android Support Library (now AndroidX) provides backward-compatible features for older Android versions.

### Why introduced?

* New APIs not available in old Android versions
* Consistent behavior across devices

### Example

```gradle
implementation "androidx.appcompat:appcompat:1.6.1"
```

---

## 1️⃣8️⃣ What is Doze Mode? What is App Standby?

### 🔹 Doze Mode

Introduced in Android 6.0 to save battery when the device is idle.

### Effects

* Restricts background CPU and network usage
* Delays jobs and alarms

---

### 🔹 App Standby

Restricts background activities of unused apps.

### Effects

* Limits background execution
* Saves battery

---

## 1️⃣9️⃣ What is File, Class, and Activity in Android?

### 🔹 File

A file is a physical resource stored in the project (e.g., XML, Kotlin, images).

Example:

* `MainActivity.kt`
* `activity_main.xml`

---

### 🔹 Class

A class is a blueprint for objects in Java/Kotlin.

Example:

```kotlin
class User(val name: String)
```

---

### 🔹 Activity

An Activity is a UI component representing a screen.

Example:

```kotlin
class MainActivity : AppCompatActivity()
```

---

## 2️⃣0️⃣ How to change parameters in an app without app update?

This can be done using **Remote Configuration techniques**.

### Common Methods

1. Firebase Remote Config
2. Server API configuration
3. Feature flags
4. Remote JSON config

### Example (Firebase Remote Config)

* Change UI text, features, or behavior without updating the app.

### Benefits

* Dynamic updates
* A/B testing
* Feature toggling

---

//here is other one

---

## 1️⃣ What is Activity and its lifecycle?

An **Activity** is a core Android component that represents a single screen with a user interface.

### Activity Lifecycle Methods

```kotlin
onCreate()   // Activity created
onStart()    // Activity becomes visible
onResume()   // Activity in foreground (interactive)
onPause()    // Activity partially visible
onStop()     // Activity no longer visible
onDestroy()  // Activity destroyed
onRestart()  // Activity restarting after stop
````

### Lifecycle Flow

```
onCreate → onStart → onResume
                ↓
            onPause → onStop → onDestroy
```

---

## 2️⃣ Difference between onCreate() and onStart()

| onCreate()                           | onStart()                                  |
| ------------------------------------ | ------------------------------------------ |
| Called once when Activity is created | Called every time Activity becomes visible |
| Used for initialization              | Used to prepare UI                         |
| Set content view                     | Register listeners                         |

---

## 3️⃣ When is only onDestroy() called without onPause() and onStop()?

⚠️ In normal lifecycle flow, `onDestroy()` is **not called alone**.
However, it may be called directly when:

* System kills the process
* finish() is called before Activity is fully resumed
* App crashes

✅ Note: Android does not guarantee `onDestroy()` execution.

---

## 4️⃣ Activity lifecycle when launched for the first time

```
onCreate → onStart → onResume
```

---

## 5️⃣ Activity lifecycle when back button is pressed

```
onPause → onStop → onDestroy
```

---

## 6️⃣ Activity lifecycle when launched again after back press

A new instance is created:

```
onCreate → onStart → onResume
```

---

## 7️⃣ Activity lifecycle when home button is pressed

```
onPause → onStop
```

(Activity is kept in back stack, not destroyed)

---

## 8️⃣ Activity lifecycle when app returns from background

```
onRestart → onStart → onResume
```

---

## 9️⃣ Lifecycle when navigating from Activity A → Activity B

```
Activity A: onPause()
Activity B: onCreate → onStart → onResume
Activity A: onStop()
```

---

## 🔟 Lifecycle when pressing back from Activity B → Activity A

```
Activity B: onPause → onStop → onDestroy
Activity A: onRestart → onStart → onResume
```

---

## 1️⃣1️⃣ How to preserve activity state during screen rotation?

Use:

* `onSaveInstanceState()`
* ViewModel
* SavedStateHandle

### Example

```kotlin
override fun onSaveInstanceState(outState: Bundle) {
    outState.putString("name", "Aasim")
    super.onSaveInstanceState(outState)
}
```

---

## 1️⃣2️⃣ What is savedInstanceState Bundle?

`savedInstanceState` is a Bundle that stores UI state before Activity destruction.

### Example

```kotlin
override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    val name = savedInstanceState?.getString("name")
}
```

---

## 1️⃣3️⃣ Difference between Intent and Bundle

| Intent                   | Bundle                  |
| ------------------------ | ----------------------- |
| Used to start components | Used to pass data       |
| Can carry Bundle         | Cannot start components |
| Messaging object         | Key-value container     |

---

## 1️⃣4️⃣ What are launchModes?

Launch modes define how Activities are created and managed in the back stack.

### Types

* standard (default)
* singleTop
* singleTask
* singleInstance

---

## 1️⃣5️⃣ Explain standard launchMode

* Default mode
* Always creates a new instance

### Back stack example

```
A → B → C → B (new instance)
```

---

## 1️⃣6️⃣ Explain singleTop launchMode

* Reuses Activity if already on top of stack

### Example

```
A → B → C → B (reuse if B is on top)
```

---

## 1️⃣7️⃣ Explain singleTask launchMode

* Only one instance exists in a task
* Clears above Activities

### Example

```
A → B → C → D → B
Result: A → B
```

---

## 1️⃣8️⃣ Explain singleInstance launchMode

* Activity runs in a separate task
* No other Activity in the same task

---

## 1️⃣9️⃣ What are tasks and back stack?

### Task

A task is a collection of Activities that users interact with.

### Back Stack

A stack of Activities in LIFO order.

---

## 2️⃣0️⃣ What is taskAffinity?

taskAffinity defines which task an Activity prefers to belong to.

### Example

```xml
<activity
    android:name=".MainActivity"
    android:taskAffinity="com.example.newtask" />
```

---

## 2️⃣1️⃣ What is installLocation tag?

Specifies where the app can be installed.

### Values

* auto
* internalOnly
* preferExternal

```xml
<manifest android:installLocation="auto">
```

---

## 2️⃣2️⃣ Relationship between Activity and Fragment lifecycle

Fragments have their own lifecycle but depend on Activity.

### Example mapping

| Activity    | Fragment                      |
| ----------- | ----------------------------- |
| onCreate()  | onAttach() → onCreate()       |
| onStart()   | onStart()                     |
| onResume()  | onResume()                    |
| onPause()   | onPause()                     |
| onStop()    | onStop()                      |
| onDestroy() | onDestroyView() → onDestroy() |

---

## 2️⃣3️⃣ How do we save and restore an activity's state during screen rotation?

### Steps

1. Save state in `onSaveInstanceState()`
2. Restore state in `onCreate()` or `onRestoreInstanceState()`

---

## 2️⃣4️⃣ What is a Bundle?

A Bundle is a key-value pair data structure used to pass data between Android components.

### Example

```kotlin
val bundle = Bundle()
bundle.putInt("age", 25)
```

---

## 2️⃣5️⃣ When Activity A starts Activity B, explain the lifecycle order

```
Activity A: onPause()
Activity B: onCreate → onStart → onResume
Activity A: onStop()
```

---

## 2️⃣6️⃣ How do you declare the launch mode in your application?

### In AndroidManifest.xml

```xml
<activity
    android:name=".MainActivity"
    android:launchMode="singleTask" />
```

### In Intent

```kotlin
intent.addFlags(Intent.FLAG_ACTIVITY_SINGLE_TOP)
```

---

## 2️⃣7️⃣ How to know configChange happens in onDestroy?

Use `isChangingConfigurations`.

### Example

```kotlin
override fun onDestroy() {
    super.onDestroy()
    if (isChangingConfigurations) {
        Log.d("ConfigChange", "Activity destroyed due to configuration change")
    }
}
```

---


//fragment


---

## 1️⃣ What is Fragment?

A **Fragment** is a reusable portion of UI that represents a part of an Activity’s interface and behavior.

### Key Points
- Fragment cannot exist without an Activity.
- It has its own lifecycle.
- Used for modular and reusable UI.
- Supports multi-pane layouts (tablet, foldables).

### Example
```kotlin
class HomeFragment : Fragment(R.layout.fragment_home)
````

---

## 2️⃣ Fragment Lifecycle

Fragments have a lifecycle similar to Activities but with additional callbacks.

### Lifecycle Methods

```kotlin
onAttach()        // Fragment attached to Activity
onCreate()        // Fragment created
onCreateView()    // UI created
onViewCreated()   // View ready
onStart()         // Fragment visible
onResume()        // Fragment active
onPause()         // Fragment partially visible
onStop()          // Fragment hidden
onDestroyView()   // View destroyed
onDestroy()       // Fragment destroyed
onDetach()        // Fragment detached from Activity
```

---

## 3️⃣ Why is it recommended to use only the default constructor in Fragment?

Fragments must have a **public empty constructor** because Android may recreate them during configuration changes or process death.

### ❌ Wrong Approach

```kotlin
class MyFragment(val name: String) : Fragment()
```

### ✅ Correct Approach

Use `newInstance()` with Bundle.

```kotlin
class MyFragment : Fragment() {

    companion object {
        fun newInstance(name: String): MyFragment {
            val fragment = MyFragment()
            val bundle = Bundle()
            bundle.putString("name", name)
            fragment.arguments = bundle
            return fragment
        }
    }
}
```

---

## 4️⃣ Fragment lifecycle when launched

```
onAttach → onCreate → onCreateView → onViewCreated → onStart → onResume
```

---

## 5️⃣ Fragment lifecycle when back button is pressed

If Fragment is in back stack:

```
onPause → onStop → onDestroyView
```

If Fragment is removed completely:

```
onPause → onStop → onDestroyView → onDestroy → onDetach
```

---

## 6️⃣ Fragment lifecycle when home button is pressed

```
onPause → onStop
```

(Fragment remains in memory)

---

## 7️⃣ Fragment lifecycle when returning from background

```
onStart → onResume
```

---

## 8️⃣ Difference between Fragment and Activity

| Fragment            | Activity                |
| ------------------- | ----------------------- |
| Part of an Activity | Independent component   |
| Cannot exist alone  | Can exist independently |
| Lightweight         | Heavy component         |
| Reusable UI         | Full screen UI          |
| Child of Activity   | Parent container        |

---

## 9️⃣ When should you use Fragment instead of Activity?

Use Fragment when:

* Building modular UI
* Supporting multiple screen sizes
* Implementing single-activity architecture
* Reusing UI components
* Using ViewPager / Navigation Component

---

## 🔟 Difference between add and replace Fragment in back stack

### add()

* Adds Fragment on top of existing Fragment
* Previous Fragment remains in memory and visible (if not hidden)

### replace()

* Removes current Fragment and adds new Fragment
* Previous Fragment is destroyed (view)

| add()                      | replace()                   |
| -------------------------- | --------------------------- |
| Multiple fragments coexist | Only one fragment at a time |
| Faster UI switching        | Cleaner UI                  |
| More memory usage          | Less memory usage           |

---

## 1️⃣1️⃣ What is Retained Fragment / Headless Fragment?

A **Retained Fragment** is a Fragment that survives configuration changes.

### Characteristics

* No UI (Headless Fragment)
* Used to retain data across configuration changes

### Example

```kotlin
setRetainInstance(true)
```

⚠️ Deprecated in modern Android → replaced by ViewModel.

---

## 1️⃣2️⃣ Purpose of addToBackStack() in FragmentTransaction

`addToBackStack()` adds a Fragment transaction to the back stack, allowing users to navigate back.

### Example

```kotlin
supportFragmentManager.beginTransaction()
    .replace(R.id.container, SecondFragment())
    .addToBackStack(null)
    .commit()
```

### Without addToBackStack()

* Back button closes Activity.

---

## 1️⃣3️⃣ How to communicate between two Fragments?

### ✅ Best Approaches

#### 1. Shared ViewModel (Recommended)

* Both fragments share same ViewModel.

#### 2. Interface Callback

* Fragment communicates via Activity.

#### 3. Fragment Result API

* Modern solution.

### Example (Fragment Result API)

```kotlin
parentFragmentManager.setFragmentResult("key", bundleOf("data" to "Hello"))
```

---

## 1️⃣4️⃣ How to share ViewModel between fragments?

Use `activityViewModels()`.

### Example

```kotlin
class SharedViewModel : ViewModel() {
    val data = MutableLiveData<String>()
}
```

```kotlin
val viewModel: SharedViewModel by activityViewModels()
```

---

## 1️⃣5️⃣ Difference between Dialog and DialogFragment

| Dialog               | DialogFragment                 |
| -------------------- | ------------------------------ |
| UI popup component   | Fragment wrapper around Dialog |
| Not lifecycle-aware  | Lifecycle-aware                |
| Manual management    | Managed by FragmentManager     |
| Risk of memory leaks | Safer                          |

### Example DialogFragment

```kotlin
class MyDialogFragment : DialogFragment()
```

---



///intent

---

# ✅ Android Intent & Broadcast – Explained with Tags + Examples

---

## 1) What is Intent?

✅ **Definition:**
Intent is a messaging object used to request an action from another component (Activity, Service, BroadcastReceiver).

✅ **Used Class / Tag:**
`android.content.Intent`

✅ **Example:**

```kotlin
val intent = Intent(this, SecondActivity::class.java)
startActivity(intent)
```

---

## 2) What is Explicit Intent?

✅ **Definition:**
Intent where you specify the exact target component (class name).

✅ **Used Class:**
`Intent(Context, TargetClass::class.java)`

✅ **Example:**

```kotlin
val intent = Intent(this, ProfileActivity::class.java)
startActivity(intent)
```

---

## 3) What is Implicit Intent?

✅ **Definition:**
Intent where the target component is not specified, but the action is defined.

✅ **Used Tags / Actions:**
`Intent.ACTION_VIEW`, `Intent.ACTION_SEND`

✅ **Example:**

```kotlin
val intent = Intent(Intent.ACTION_VIEW)
intent.data = Uri.parse("https://google.com")
startActivity(intent)
```

---

## 4) What is Sticky Intent?

✅ **Definition:**
Sticky Intent remains in the system after being broadcast, so future receivers can access it.

⚠️ Deprecated in modern Android.

✅ **Used Method:**
`sendStickyBroadcast()`

✅ **Example (Not recommended):**

```kotlin
val intent = Intent("MY_ACTION")
sendStickyBroadcast(intent)
```

---

## 5) What is PendingIntent?

✅ **Definition:**
A token that allows another app or system to execute your Intent later on your behalf.

✅ **Used Class:**
`android.app.PendingIntent`

✅ **Example:**

```kotlin
val intent = Intent(this, MainActivity::class.java)
val pendingIntent = PendingIntent.getActivity(
    this, 0, intent, PendingIntent.FLAG_UPDATE_CURRENT
)
```

📌 Used in: Notifications, Alarms, Widgets.

---

## 6) What is IntentFilter?

✅ **Definition:**
Declares which Intents a component can respond to.

✅ **Used Tag (Manifest):**
`<intent-filter>`

✅ **Example (AndroidManifest.xml):**

```xml
<activity android:name=".MainActivity">
    <intent-filter>
        <action android:name="android.intent.action.MAIN"/>
        <category android:name="android.intent.category.LAUNCHER"/>
    </intent-filter>
</activity>
```

---

## 7) What is BroadcastReceiver?

✅ **Definition:**
A component that listens for system-wide or app-specific broadcast messages.

✅ **Used Class:**
`BroadcastReceiver`

✅ **Example:**

```kotlin
class MyReceiver : BroadcastReceiver() {
    override fun onReceive(context: Context, intent: Intent) {
        Log.d("Receiver", "Broadcast received")
    }
}
```

Register in Manifest:

```xml
<receiver android:name=".MyReceiver"/>
```

---

## 8) What is LocalBroadcastManager?

✅ **Definition:**
Used to send broadcasts within the same app only (more secure & efficient).

⚠️ Deprecated → Use Flow / LiveData / SharedViewModel instead.

✅ **Used Class:**
`LocalBroadcastManager`

✅ **Example:**

```kotlin
LocalBroadcastManager.getInstance(this)
    .sendBroadcast(Intent("MY_LOCAL_ACTION"))
```

---

## 9) Types of Broadcasts in Android

### ✅ a) Normal Broadcast

* Delivered to all receivers simultaneously.

### ✅ b) Ordered Broadcast

* Delivered one by one based on priority.

### ✅ c) Sticky Broadcast

* Remains in system memory.

### ✅ d) Local Broadcast

* Inside the same app only.

---

## 10) Difference between Normal vs Ordered Broadcast

| Feature              | Normal Broadcast | Ordered Broadcast      |
| -------------------- | ---------------- | ---------------------- |
| Delivery             | Simultaneous     | Sequential             |
| Priority             | No               | Yes                    |
| Can stop propagation | ❌ No             | ✅ Yes                  |
| Method               | sendBroadcast()  | sendOrderedBroadcast() |

✅ Example:

```kotlin
sendBroadcast(Intent("ACTION_NORMAL"))
sendOrderedBroadcast(Intent("ACTION_ORDERED"), null)
```

---

## 11) How can two Android apps interact?

✅ Methods:

### ✅ a) Implicit Intent

```kotlin
val intent = Intent(Intent.ACTION_SEND)
intent.type = "text/plain"
startActivity(intent)
```

### ✅ b) Content Provider

* Share data using URI.

### ✅ c) BroadcastReceiver

* App-to-app communication.

### ✅ d) Deep Links

* Open another app using URL.

---

## 12) What is Deeplink?

✅ **Definition:**
A URL that opens a specific screen inside an app instead of the browser.

✅ **Used Tags:**
`<data>`, `<intent-filter>`

✅ **Example (Manifest):**

```xml
<activity android:name=".ProductActivity">
    <intent-filter>
        <action android:name="android.intent.action.VIEW"/>
        <category android:name="android.intent.category.DEFAULT"/>
        <category android:name="android.intent.category.BROWSABLE"/>

        <data
            android:scheme="https"
            android:host="myapp.com"
            android:pathPrefix="/product"/>
    </intent-filter>
</activity>
```

✅ Open link:

```
https://myapp.com/product/123
```

---
//service

---

# ✅ Android Service & Background Processing – Explained with Tags + Examples

---

## 1) What is Service?

✅ **Definition:**
A Service is an Android component that performs long-running operations in the background without UI.

✅ **Used Class:**
`android.app.Service`

✅ **Example:**

```kotlin
class MyService : Service() {
    override fun onBind(intent: Intent?): IBinder? = null

    override fun onStartCommand(intent: Intent?, flags: Int, startId: Int): Int {
        Log.d("Service", "Service Started")
        return START_STICKY
    }
}
```

Start Service:

```kotlin
startService(Intent(this, MyService::class.java))
```

---

## 2) Types of Services in Android

### ✅ a) Foreground Service

### ✅ b) Background Service (Deprecated / Restricted)

### ✅ c) Bound Service

---

## 3) What is Foreground Service?

✅ **Definition:**
A service that runs in the foreground with a visible notification.

✅ **Used Methods:**
`startForeground()`

✅ **Example:**

```kotlin
startForeground(1, notification)
```

📌 Use cases:
Music player, navigation, fitness tracking, location tracking.

---

## 4) What is Background Service?

✅ **Definition:**
A service running in the background without user interaction.

⚠️ Restricted from Android 8+ (Oreo).

📌 Reason: Battery optimization & security.

---

## 5) What is Bound Service?

✅ **Definition:**
A service that allows components to bind and interact with it.

✅ **Used Method:**
`bindService()`

✅ **Example:**

```kotlin
bindService(Intent(this, MyService::class.java), connection, Context.BIND_AUTO_CREATE)
```

---

## 6) Difference between Service and IntentService

| Feature            | Service            | IntentService     |
| ------------------ | ------------------ | ----------------- |
| Thread             | Main thread        | Background thread |
| Queue              | ❌ No               | ✅ Yes             |
| Stop automatically | ❌ No               | ✅ Yes             |
| Use case           | Long-running tasks | Sequential tasks  |

---

## 7) Why IntentService is deprecated?

✅ Reasons:

* Not lifecycle-aware
* No support for modern background limits
* Replaced by WorkManager / JobIntentService / Coroutines

⚠️ Deprecated since Android API 30.

---

## 8) What is JobIntentService?

✅ **Definition:**
A backward-compatible alternative to IntentService using JobScheduler.

✅ **Used Class:**
`androidx.core.app.JobIntentService`

✅ **Example:**

```kotlin
class MyJobIntentService : JobIntentService() {
    override fun onHandleWork(intent: Intent) {
        Log.d("JobIntentService", "Task executed")
    }
}
```

---

## 9) What is JobScheduler?

✅ **Definition:**
API to schedule background jobs based on conditions (network, charging, idle).

✅ **Used Class:**
`android.app.job.JobScheduler`

✅ **Example:**

```kotlin
val jobInfo = JobInfo.Builder(1, ComponentName(this, MyJobService::class.java))
    .setRequiredNetworkType(JobInfo.NETWORK_TYPE_ANY)
    .build()
```

---

## 10) What is WorkManager?

✅ **Definition:**
A modern Android library for guaranteed background work execution.

✅ **Used Class:**
`androidx.work.WorkManager`

✅ **Example:**

```kotlin
val workRequest = OneTimeWorkRequestBuilder<MyWorker>().build()
WorkManager.getInstance(this).enqueue(workRequest)
```

📌 Best for:

* Guaranteed execution
* Deferrable tasks
* Background sync

---

## 11) Foreground Service vs WorkManager

| Feature              | Foreground Service | WorkManager |
| -------------------- | ------------------ | ----------- |
| Runs immediately     | ✅ Yes              | ❌ No        |
| Visible notification | ✅ Yes              | ❌ No        |
| Guaranteed execution | ❌ No               | ✅ Yes       |
| Long-running task    | ✅ Yes              | ⚠️ Limited  |
| Battery-friendly     | ❌ No               | ✅ Yes       |

✅ Rule:

* Real-time task → Foreground Service
* Deferred task → WorkManager

---

## 12) How to get continuous location updates?

✅ Best approaches:

### ✅ a) Foreground Service + FusedLocationProvider

```kotlin
val locationRequest = LocationRequest.create()
    .setInterval(5000)
    .setPriority(LocationRequest.PRIORITY_HIGH_ACCURACY)
```

### ✅ b) WorkManager (not real-time)

### ✅ c) Callback-based Location API

📌 Recommended: Foreground Service.

---

## 13) What can be used for background processing in Android?

✅ Options:

| Tool                     | Use Case             |
| ------------------------ | -------------------- |
| Thread / ExecutorService | Short tasks          |
| Coroutine                | Modern async tasks   |
| HandlerThread            | Background thread    |
| Service                  | Long-running tasks   |
| Foreground Service       | Real-time tasks      |
| WorkManager              | Guaranteed tasks     |
| JobScheduler             | System-managed jobs  |
| AlarmManager             | Scheduled tasks      |
| RxJava                   | Reactive async tasks |

---












