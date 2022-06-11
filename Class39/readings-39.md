# Class-39 : Kinesis


In this file I will be summarizing what I have learnt in class-39 reading notes which included the following resources :
- [Location](https://developer.android.com/training/location/retrieve-current).

## Location
***
When you create your application and you want to use your user's current location , you can do that using the Google Play services location APIs using the fused location provider to retrieve the device's last known location.

### How?
1. Set up Google Play services :
    - Download and install the Google Play services component via the SDK Manager and add the library to your project. 
2. Specify app permissions 
3. Create location services client : inside `onCreate()` method, create an instance of the Fused Location Provider Client as the following code :
````
private FusedLocationProviderClient fusedLocationClient;

// ..

@Override
protected void onCreate(Bundle savedInstanceState) {
    // ...

    fusedLocationClient = LocationServices.getFusedLocationProviderClient(this);
}
````

4. Get the last known location : use `getLastLocation() `method which returns a Task that you can use to get a Location object with the latitude and longitude coordinates of a geographic location.  
The following code snippet illustrates the request and a simple handling of the response: 
`````
fusedLocationClient.getLastLocation()
        .addOnSuccessListener(this, new OnSuccessListener<Location>() {
            @Override
            public void onSuccess(Location location) {
                // Got last known location. In some rare situations this can be null.
                if (location != null) {
                    // Logic to handle location object
                }
            }
        });
`````
 The location object may be null in the following situations:
 - Location is turned off in the device settings.
 - The device never recorded its location.
 - Google Play services on the device has restarted so there is no active Fused Location Provider client that has requested location after the services restarted.

5. Choose the best location estimate : Choose from one of the following, depending on your app's use case:
    - `getLastLocation()` : works fast , minimizes battery usage and location information might be out of date.
    - `getCurrentLocation()` : more accurate location more consistently , can cause active location computation to occur on the device.
    - `requestLocationUpdates()` : **Most recommended way** gets a fresh location, and is safer *but* your app can sometimes consume large amounts of power if location isn't available, or if the request isn't stopped correctly after obtaining a fresh location.