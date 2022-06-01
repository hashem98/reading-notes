# Amplify and Kinesis

The Analytics category enables you to collect analytics data for your App and it's built-in support for Amazon Kinesis

## Set up Analytics backend
1. `amplify add analytics`
2. `amplify push`
3. Install Amplify Libraries
4. Initialize Amplify Analytics
5. To record an event, create an `AnalyticsEvent` and call `Amplify.Analytics.recordEvent()`
6. `amplify console analytics`


## Record events 
we can record custom events within the app
* Events have default configuration to flush out to the network every 30 seconds
* we can register global properties which will be sent along with all invocations of `Amplify.Analytics.recordEvent`
* To disable analytics, call:``Amplify.Analytics.disable();`

* it's Automatically track sessions by `amplify console analytics`

* Identify user call sends information that you have specified about the user to Amazon Pinpoint. This could be for an unauthenticated or an authenticated user.

* we can retrieve the escape hatch to access the underlying Amazon Pinpoint client

* Existing Amazon Pinpoint resources can be used with the Amplify Libraries by referencing your Application ID and Region in your amplifyconfiguration.json file



[resources](https://docs.amplify.aws/lib/analytics/getting-started/q/platform/android/)