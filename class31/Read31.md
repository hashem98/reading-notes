# Espresso

Espresso is a test automation tool for Android applications developed by Google.

### Create UI tests with Espresso Test Recorder

this tool allow  you to test your app by snapshots of you app then Espresso takes the saved recording and automatically generates a corresponding UI test that you can run to test your app

* Before using Espresso Test Recorder, make sure you turn off animations on your test device

### Record an Espresso test

1. UI interactions : it's include actions that a person may use to interact with the app

 * Click Run > Record Espresso Test.
 
 * In the Select Deployment Target window, choose the device on which you want to record the test then OK
 
 * the app must install and launch before Espresso Test Recorder allows you to interact with it

2. assertions on View elements : verify the existence or contents of visual elements on the screen by three types .

 * text is: Checks the text  content of the selected View  element
 * exists: Checks that the View  element is present in the  current View hierarchy visible on the screen
 * does not exist: Checks that  the View element is not  present in the current View  hierarchy

 1. Click Add Assertion. A Screen Capture dialog appears while Espresso gets the UI hierarchy

 2.  click on the element in the screenshot or use the first drop-down menu in the Edit assertion box at the bottom of the window.

 3. in the Edit assertion box select the assertion 

 4. click Save Assertion

 5. Click Complete Recording then save 

 6. The file automatically opens after Espresso Test Recorder generates it we can see it in ` src > androidTest > java >`


### Run an Espresso test locally


1. use the Project  window on the left side of the Android Studio IDE
2. open app module and choose the test 
3.  click Run ‘testName.’
4. In the Select Deployment Target window, choose the device then click ok