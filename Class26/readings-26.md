# Class-26 : Android fundamentals
***

In this file I will be summarizing what I have learnt in class-27 reading notes which included the following resources : 
- [Android fundamentals](https://developer.android.com/guide/components/fundamentals).

## Android fundamentals
***
**Android apps** can be written using *Kotlin, Java, and C++* languages.  
**An Android package** (`.apk` file) contains the contents of an Android app that are required at runtime and it is the file that Android-powered devices use to install the app.  
**An Android App Bundle** (`.aab` file)  contains the contents of an Android app project including some additional metadata that is not required at runtime and is not installable on Android devices.    
The Android system implements the principle of **least privilege**. That is, each app, by default, has access only to the components that it requires to do its work and no more , which makes it more secure to not have access to not given permission files and not needed ones.   
**How do we to share data with other apps ?**  
1.  share the same Linux user ID.
2.  request permission to access device data. 
[Working with System Permissions](https://developer.android.com/training/permissions)

### App components
Application conmponents are the basic building blocks for an android application , they make the user able to enter the application and use it . 
#### Activities
An activity is every single screen or user interface in the application. interactions between the system and the application are listed as follows : 
- keeping track to what activity is on the screen.
- knowing stopped activities that the user may get back to.
- Help the application find those stopped activities when the user get back to the application.
- Handle interaction between different applications like using the camera inside the application or even sharing to another application. 
#### Services
A servise is what keeps our applications running in the background of our systems like playing music from an application while working on another one.   
There are two types of services that tell the system how to manage an app: 
- **Started services** , which the system keep them running until their work is done , it has two types :
    - Started services under the awareness of the user such as playing music , the system keeps such services running because the user is aware of them if they stopped suddenly. 
    - Started services without the awareness of the user like any regular backgroud service , the system has mmore freedom with dealing with them since the user is not really aware about them so it might kill it and restart it according to the sitation of the device. 
- **Bound services** , which the system or some other application asks to run it because it needs to use its service , so the system keeps it running as long as it is needed from the system or the other application. 

#### Broadcast receivers
A broadcast receiver is a component that enables the system to deliver events to another application, allowing the application to respond to system-wide broadcast announcements , Like setting an alarm from a scheduling application . Thus ,you may create a status bar notification to alert the user when a broadcast event occurs. 
#### Content providers
A content provider manages a shared set of app data that you can store in the file system so  apps can query or modify the data if the content provider allows it. you can think of a content provider as an abstraction on a database.
#### Activating components 
Components can be activated using the `Intent` object which has two types :
- explicit intent : defines a message to activate a specific component.
- implicit intent : defines a message to activate a specific type of component. 

Unlike activities, services, and broadcast receivers, **content providers are not activated by intents**, they need to be targeted by a request from a `ContentResolver`.
### The manifest file
The manifest file `AndroidManifest.xml` makes the system knows that the component exists, so we must declare all components in that file which is in the root of the project directory.   
The manifest does :
- declaring the app's components.
- Identifies user permissions the app requires.
- Declares the minimum API Level required by the app, based on which APIs the app uses.
- Declares hardware and software features used or required by the app.
- Declares API libraries the app needs to be linked against (other than the Android framework APIs), such as the Google Maps library.
#### Declaring components
In general ,you must declare all application components using the following elements:

- <activity> elements for activities.
- <service> elements for services.
- <receiver> elements for broadcast receivers.
- <provider> elements for content providers.

Any component that is not declared in the manifest file won't be visible to the system.
**Example:**

```
<?xml version="1.0" encoding="utf-8"?>
<manifest ... >
    <application android:icon="@drawable/app_icon.png" ... >
        <activity android:name="com.example.project.ExampleActivity"
                  android:label="@string/example_label" ... >
        </activity>
        ...
    </application>
</manifest>
````

#### Declaring component capabilities
**ُExample :**
if you build an email app with an activity for composing a new email, you can declare an intent filter to respond to "send" intents (in order to send a new email), as shown in the following example:
```
<manifest ... >
    ...
    <application ... >
        <activity android:name="com.example.project.ComposeEmailActivity">
            <intent-filter>
                <action android:name="android.intent.action.SEND" />
                <data android:type="*/*" />
                <category android:name="android.intent.category.DEFAULT" />
            </intent-filter>
        </activity>
    </application>
</manifest>
```

#### Declaring app requirements
**For example**, if your app requires a camera and uses APIs introduced in Android 8.0 (API Level 26), you must declare these requirements inside your `build.gradle` file :
```
android {
  ...
  defaultConfig {
    ...
    minSdkVersion 26
    targetSdkVersion 29
  }
}
```
Declare the camera feature directly in your app's manifest file:

```
<manifest ... >
    <uses-feature android:name="android.hardware.camera.any"
                  android:required="true" />
    ...
</manifest>
```
With the declarations shown in these examples, devices that do not have a camera or have an Android version lower than 8.0 cannot install your app from Google Play. 

