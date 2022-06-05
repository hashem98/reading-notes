# Allowing Other Apps to Start Your Activity 


*ACTION_SEND* intent :it's action that support share content and your app should appear in share list .
1. add `<intent-filter>`

## Add an Intent Filter

criteria of the Intent object
1. Action: A string naming the action to perform. Usually one of the platform-defined values such as ACTION_SEND or ACTION_VIEW

2. Data : `<data>` A description of the data associated with the intent

3. Category :`<category>` Provides an additional way to characterize the activity handling the intent

* Each incoming intent specifies only one action and one data type, but it's OK to declare multiple instances of the `<action>`, `<category>`, and `<data>` elements in each `<intent-filter>`

* If any two pairs of action and data are mutually exclusive in their behaviors, you should create separate intent filters to specify which actions are acceptable when paired with which data types

## Handle the Intent in Your Activity

As your activity starts, call `getIntent()` to retrieve the Intent that started the activity. You can do so at any time during the lifecycle of the activity, but you should generally do so during early callbacks such as `onCreate()` or `onStart()`

## Return a Result

call `setResult()` to specify the result code and result Intent. When your operation is done and the user should return to the original activity, call `finish()` to close (and destroy) your activity

*  Generally, it's either `RESULT_OK` or `RESULT_CANCELED`. You can then provide additional data with an Intent

