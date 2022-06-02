# Class-38 : Notifications


In this file I will be summarizing what I have learnt in class-38 reading notes which included the following resources :
- [Intent Filters](https://developer.android.com/training/basics/intents/filters).
- [Implicit vs. Explicit Intents](https://developer.android.com/guide/components/intents-filters#Types).

## Intent Filters 
***
If an apllication performs a useful action that other applications can use , the application should be prepared to response to these applications requests by specifying the appropriate intent filter.

### How ?
by adding an `<intent-filter>` element in your manifest file for the corresponding `<activity>` element.   
An intent consists of : 
- Action : A string naming the action to perform. 
- Data : A description of the data associated with the intent.
- Category : Provides an additional way to characterize the activity handling the intent, usually related to the user gesture or location from which it's started. 

#### Example : 
here's an activity with an intent filter that handles the ACTION_SEND intent when the data type is either text or an image:
```
<activity android:name="ShareActivity">
    <intent-filter>
        <action android:name="android.intent.action.SEND"/>
        <category android:name="android.intent.category.DEFAULT"/>
        <data android:mimeType="text/plain"/>
        <data android:mimeType="image/*"/>
    </intent-filter>
</activity>
```

### Handle the Intent in Your Activity 
As your activity starts, call getIntent() to retrieve the Intent that started the activity. 
```
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);

    setContentView(R.layout.main);

    // Get the intent that started this activity
    Intent intent = getIntent();
    Uri data = intent.getData();

    // Figure out what to do based on the intent type
    if (intent.getType().indexOf("image/") != -1) {
        // Handle intents with image data ...
    } else if (intent.getType().equals("text/plain")) {
        // Handle intents with text ...
    }
}
```
### Return a Result 

If you want to return a result to the activity that invoked yours, simply call `setResult()` and send the result code and result Intent. 
Then when the operation is done call `finish()`.
You must always specify a result code with the result. Generally, it's either `RESULT_OK` or `RESULT_CANCELED`.  
Example :   
``` 
// Create intent to deliver some kind of result data
Intent result = new Intent("com.example.RESULT_ACTION", Uri.parse("content://result_uri"));
setResult(Activity.RESULT_OK, result);
finish();
```

## Implicit vs. Explicit Intents 
***

![Implicit vs. Explicit Intents ](https://miro.medium.com/max/1400/1*8lcojsn8SFzKrPO29GmM4g.png)