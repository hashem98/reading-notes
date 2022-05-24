# Amplify and Cognito


The Auth category can be used to register a user, confirm attributes like email/phone, and sign in with optional multi-factor authentication.

### Configure Auth Category

- start `amplify add auth`
- push `amplify push`
- add dependency ` implementation 'com.amplifyframework:aws-auth-cognito:1.24.0'`
- Add the `Auth plugin` before calling `Amplify.configure`

### Register a user
invoke 

```
AuthSignUpOptions options = AuthSignUpOptions.builder()
    .userAttribute(AuthUserAttributeKey.email(), "my@email.com")
    .build();
Amplify.Auth.signUp("username", "Password123", options,
    result -> Log.i("AuthQuickStart", "Result: " + result.toString()),
    error -> Log.e("AuthQuickStart", "Sign up failed", error)
);

```


- Enter the confirmation code received via email in the `confirmSignUp`

### Sign in a user
calling this method 

```
Amplify.Auth.signIn(
    "username",
    "password",
    result -> Log.i("AuthQuickstart", result.isSignInComplete() ? "Sign in succeeded" : "Sign in not complete"),
    error -> Log.e("AuthQuickstart", error.toString())
);
```

### Sign in with web UI

-  run `amplify update auth`
-  run` amplify push`
- Update AndroidManifest.xml
- Add Response Handler
- Launch Web UI Sign In
```
Amplify.Auth.signInWithWebUI(
    this,
    result -> Log.i("AuthQuickStart", result.toString()),
    error -> Log.e("AuthQuickStart", error.toString())
);


```

*  AWS Cognito Auth Plugin can be configured to automatically obtain guest credentials once the device is online so that you are able to use other categories "anonymously" without the need to sign in. You will not be able to perform user specific methods while in this state such as updating attributes, changing your password, or getting the current user. However, you can obtain the unique Identity ID which is assigned to the device through the fetchAuthSession

### User attributes

- Invoke the following to get the list of attributes assigned to the user
```
Amplify.Auth.fetchUserAttributes(
    attributes -> Log.i("AuthDemo", "User attributes = " + attributes.toString()),
    error -> Log.e("AuthDemo", "Failed to fetch user attributes.", error)
);
```
- Update user attribute by call `updateUserAttribute`
- Verify user attribute
- Resend verification code

### Sign out
- Invoke the signOut api
```
Amplify.Auth.signOut(
    () -> Log.i("AuthQuickstart", "Signed out successfully"),
    error -> Log.e("AuthQuickstart", error.toString())
);
```
