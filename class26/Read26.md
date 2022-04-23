# Application Fundamentals

**Android package (APK)**: it's archive file with an `.apk` suffix,contains the contents of an Android app that are required at runtime and it is the file that Android-powered devices use to install the app.

**Android App Bundle**: which is an archive file with an `.aab` suffix, contains the contents of an Android app project including some additional metadata that is not required at runtime

* Each Android app lives in its own security sandbox, protected by multi security features.

* Android system implements the principle of least privilege  :That is, each app, by default, has access only to the components that it requires to do its work and no more. This creates a very secure environment in which an app cannot access parts of the system for which it is not given permission

## App components
1. Activities :is the entry point for interacting with the user.
* You implement an activity as a subclass of the Activity class

2. Services : It is a component that runs in the background to perform long-running operations or to perform work for remote processes .

3. Broadcast receivers :  is a component that enables the system to deliver events to the app outside of a regular user flow, allowing the app to respond to system-wide broadcast announcements

4. Content providers :  manages a shared set of app data that you can store in the file system, in a SQLite database, on the web, or on any other persistent storage location that your app can access


## Activating components

* activities, services, and broadcast receivers are activated by an asynchronous message called an intent.
* are activated by an asynchronous message called an intent.
* For activities and services, an intent defines the action to perform and may specify the URI of the data to act on, among other things that the component being started might need to know
* For broadcast receivers, the intent simply defines the announcement being broadcast.

### methods for activating each type of component:
1. You can start an activity or give it something new to do by passing an Intent to startActivity() or startActivityForResult() (when you want the activity to return a result).

2. You can initiate a broadcast by passing an Intent to methods such as sendBroadcast(), sendOrderedBroadcast(), or sendStickyBroadcast().

3. You can perform a query to a content provider by calling query() on a ContentResolver

## The manifest file

* The primary task of the manifest is to inform the system about the app's components. 

* `AndroidManifest.xml` Your app must declare all its components in this file, which must be at the root of the app project directory

* In the` <application>` element, the `android:icon` attribute points to resources for an icon that identifies the app.

In the `<activity>` element, the `android:name` attribute specifies the fully qualified class name of the `Activity` subclass and the android:label attribute specifies a string to use as the user-visible label for the activity

we must declare all app components using the following elements:

1. `<activity>` elements for activities.
2. `<service>` elements for services.
3. `<receiver>` elements for broadcast receivers.
4. `<provider>` elements for content providers

# Declaring app requirements

* it's important that you clearly define a profile for the types of devices your app supports by declaring device and software requirements in your manifest file

* The values for minSdkVersion and targetSdkVersion are set in your app module's build.gradle file

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
* Declare the camera feature
```
<manifest ... >
    <uses-feature android:name="android.hardware.camera.any"
                  android:required="true" />
    ...
</manifest>
```

*  Using app resources makes it easy to update various characteristics of your app without modifying code. Providing sets of alternative resources enables you to optimize your app for a variety of device configurations, such as different languages and screen sizes


[resources](https://developer.android.com/guide/components/fundamentals)