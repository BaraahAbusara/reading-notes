# Class-27 : Intents, Activities, and SharedPreferences
***

In this file I will be summarizing what I have learnt in class-27 reading notes which included the following resources : 
- [Android Tasks and the Back Stack](https://developer.android.com/guide/components/activities/tasks-and-back-stack).
- [Android SharedPreferences](https://developer.android.com/training/data-storage/shared-preferences).


## Android Tasks and the Back Stack
***
**What is a Task ?**
A task is group of activities that users interact with when trying to do something in the application. 
These activities are arranged in the back stack ordered in which each activity is opened. 

### Lifecycle of a task and its back stack :
![Lifecycle of a task and its back stack ](https://developer.android.com/images/fundamentals/diagram_backstack.png)  

### Back press behavior for root launcher activities :
Root launcher declares an Intent filter with both `ACTION_MAIN` and `CATEGORY_LAUNCHER`.
default behavior for *Android 12 and higher* lets users able more quickly resume the application from a warm state, instead of having to completely restart the application from a cold state. The system moves the activity and its task to the background instead of finishing the activity.

### Background and foreground tasks

### Multiple activity instances
 
### Manage tasks

### Handle affinities

###  Clear the back stack 

### Start a task




## Android SharedPreferences
***
`SharedPreferences` APIs are used to store small collection of key-values, `SharedPreferences` is an object that can be public or private and ismade to read and write key-value pairs, not for building user interface. 

### Get a handle to shared preferences :

You can create a new shared preference file or access an existing one by calling one of these methods:
- getSharedPreferences() : user for multiple shared preference files identified by name.
```
Context context = getActivity();
SharedPreferences sharedPref = context.getSharedPreferences(
        getString(R.string.preference_file_key), Context.MODE_PRIVATE);
```
- getPreferences() : you don't need to supply a name because it belongs to an activity 
```
SharedPreferences sharedPref = getActivity().getPreferences(Context.MODE_PRIVATE);
```
- getDefaultSharedPreferences() : to get the default shared preference file for your entire app.

### Write to shared preferences :
```
SharedPreferences sharedPref = getActivity().getPreferences(Context.MODE_PRIVATE);
SharedPreferences.Editor editor = sharedPref.edit();
editor.putInt(getString(R.string.saved_high_score_key), newHighScore);
editor.apply();
```

### Read from shared preferences :
```
SharedPreferences sharedPref = getActivity().getPreferences(Context.MODE_PRIVATE);
int defaultValue = getResources().getInteger(R.integer.saved_high_score_default_key);
int highScore = sharedPref.getInt(getString(R.string.saved_high_score_key), defaultValue);
```