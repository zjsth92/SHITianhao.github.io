# Android Interview Questions

http://www.andreas-schrade.de/2017/02/23/android-interview-questions/

### What is Dalvik ?
* Dalvik is register-based VM. It is now replace by ART (Android Runtime) since Lollipop (5.0).
* Each App is running on an instance of Dalvik.

### JVM vs Dalvik
* JVM is stack based and Dalvik is register based.
* In stack based vm, the memory structure where the operands are stored is a stack structure data. Operations are carring out by popping data from stack, and pushing back the result in LIFO
* In register based VM, the memory structure is based on the registers of the CPU. There is no PUSH or POP operations. Each instruction needs to contain the address of the operands.
* Dalvik uses Dex file, and JVM consumes Java bytecode.

### ART vs Dalvik
* ART uses AOT (Ahead of time) compilation
* In ART, since the code is pre-compiled at installed time, so the installing will take a bit longer.
* Machine code requires more space than the existing bytecode.

### What is the “UI thread”?
* In comment case it is the **main** thread. It is in charge of dispatching events to the appropriate user interface widgets. 
* If the UI thread is blocked more than 5 seconds, the ANR dialog will show up.

### Intent
* An Intent is basically a message that is passed between components
* Pieces of Intent
    * Action
    * Extras
    * Component name: The name of the component to start.
    * Flag: Optional metadata for the Intent
* Implicit Intent
    * It doesn't specify the target component.
    * If multiple components are compatible. The system will show a dialog so that the user can pick which one to use.
    * If there is no compatible component then the App will crash immediately. So check with ```resolveActivity``` before sending Intent is a must.
* Explicit Intent 
    * It specifies the component by the fully-qualified class name to start.    
* PendingIntent
    * It wraps a regular Intent that specifies an action to take in the future
    * Ex: AlarmManager triggers a PendingIntent at a specific time

### What is a Service ?
* A service is an application component without user interface that can perform **long** running operations in the background.
* A Service runs in the **main thread**. All blocking operations must run in a new thread inside the service instance.
* Lifecycle: 
    * Started Service: onCreate() -> onStartCommand() -> RUNNING -> onDestroy()

    * Binded Service: onCreate() -> onBind() -> RUNNING -> onUnbind() -> onDestroy()

### What is an IntentService ?
* IntentService is a subclass of Service that uses a **worker thread** 
* IntentService stops itself automatically as soons as all tasks have been handled.
* Used for "fire and forget tasks".

### What is AsyncTask ?
* AsyncTask allows to run short operations in the background and publish results easily on the UI thread.
* It is used for **short** operations from within Activity or Fragment, such as loading big Bitmap.

### What is Handler ?
* It is used for handling an actiono on a different thread.
* It can schedule runnable to be excuted at some point in the future.

### SharedPreference
* A simple mechanism to store data in Android as a collection of key-value in a XML file.

### Content Providers
* It will share the data between applications.
