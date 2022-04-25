# Understand Tasks and Back Stack

* A task is a collection of activities that users interact with when performing a certain job. The activities are arranged in a stack—the back stack


* When the current activity starts another, the new activity is pushed on the top of the stack and takes focus. The previous activity remains in the stack, but is stopped

* When an activity stops, the system retains the current state of its user interface. When the user presses the Back button, the current activity is popped from the top of the stack (the activity is destroyed) and the previous activity resumes 

* Activities in the stack are never rearranged, only pushed and popped from the stack—pushed onto the stack when started by the current activity and popped off when the user leaves it using the Back button

* Because the activities in the back stack are never rearranged, if your app allows users to start a particular activity from more than one activity

## Managing Tasks

* by placing all activities started in succession in the same task and in a "last in, first out" stack—works great for most apps and you shouldn't have to worry about how your activities are associated with tasks or how they exist in the back stack

 the principal `<activity> `attributes you can use are:

1. `taskAffinity`
2. `launchMode`
3. `allowTaskReparenting`
4. `clearTaskOnLaunch`
5. `alwaysRetainTaskState`
6. `finishOnTaskLaunch`
And the principal intent flags you an use are:

1. `FLAG_ACTIVITY_NEW_TASK`
2. `FLAG_ACTIVITY_CLEAR_TOP`
3. `FLAG_ACTIVITY_SINGLE_TOP`

Launch modes allow you to define how a new instance of an activity is associated with the current task by ;
1. manifest file :using the `<activity>` element's `launchMode` attribute. by four mode  ("standard", "singleTop","singleTask","singleInstance").

2. intent flag : by including flags in the intent that you deliver to `startActivity()`,using this type of flags (`FLAG_ACTIVITY_NEW_TASK`,`FLAG_ACTIVITY_SINGLE_TOP`,`FLAG_ACTIVITY_CLEAR_TOP`)

## Handling affinities
The affinity indicates which task an activity prefers to belong to. By default, all the activities from the same app have an affinity for each other
* You can modify the affinity for any given activity with the taskAffinity attribute of the `<activity>` element

## Clearing the back stack

If the user leaves a task for a long time, the system clears the task of all activities except the root activity. When the user returns to the task again, only the root activity is restored. using `alwaysRetainTaskState`,`clearTaskOnLaunch`,`finishOnTaskLaunch`

## Starting a task

You can set up an activity as the entry point for a task by giving it an intent filter with `"android.intent.action.MAIN"` as the specified action and` "android.intent.category.LAUNCHER"` as the specified category

```
<activity ... >
    <intent-filter ... >
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
    ...
</activity>
```

# Save key-value data

 use the `SharedPreferences` APIs to store and retrieve simple values by calling one of these methods
 1. getSharedPreferences() :for multiple shared preference files
 2. getPreferences() : for only one shared preference file

 * If you're using the `SharedPreferences` API to save app settings, you should instead use `getDefaultSharedPreferences() `to get the default shared preference file for your entire app

 ## Write to shared preferences

```
SharedPreferences sharedPref = getActivity().getPreferences(Context.MODE_PRIVATE);
SharedPreferences.Editor editor = sharedPref.edit();
editor.putInt(getString(R.string.saved_high_score_key), newHighScore);
editor.apply();
```

## Read from shared preferences

```
SharedPreferences sharedPref = getActivity().getPreferences(Context.MODE_PRIVATE);
int defaultValue = getResources().getInteger(R.integer.saved_high_score_default_key);
int highScore = sharedPref.getInt(getString(R.string.saved_high_score_key), defaultValue);
```

[Understand Tasks and Back Stack](https://developer.android.com/guide/components/activities/tasks-and-back-stack)

[Save key-value data](https://developer.android.com/training/data-storage/shared-preferences)