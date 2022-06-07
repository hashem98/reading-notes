# Location

the app can request the last known location of the user's device. by `getLastLocation()`
* use the `fused location provider` to retrieve the device's last known location


**fused location provider**: is one of the location APIs in Google Play services. It manages the underlying location technology and provides a simple API 

1. Set up Google Play services

Download and install the Google Play services component via the SDK Manager and add the library to your project


2. Specify app permissions

Apps whose features use location services must request location permissions, depending on the use cases of those features

3. Create location services client

create an instance of the Fused Location Provider Client

4. Get the last known location

 use the fused location provider's `getLastLocation()` method to retrieve the device location and request the last known location, call the getLastLocation() method


 5. Choose the best location estimate

 * `getLastLocation()` gets a location estimate more quickly and minimizes battery usage that can be attributed to your app

 * `getCurrentLocation()` gets a fresher, more accurate location more consistently. 

 * starting and managing location updates yourself using `requestLocationUpdates()`



 