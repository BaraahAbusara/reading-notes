# Class-36 : Cognito


In this file I will be summarizing what I have learnt in class-36 reading notes which included the following resources :
- [Amplify and Cognito  : “Getting started” and “Sign in” ](https://docs.amplify.aws/lib/auth/getting-started/q/platform/android/).

## Getting started
***
Amazon Cognito lets you add user sign-up, sign-in, and access control to your web and mobile apps quickly and easily.
The Amplify Auth category provides an interface for authenticating a user. Behind the scenes, it provides the necessary authorization to the other Amplify categories. It comes with default, built-in support for Amazon Cognito User Pool and Identity Pool.
To get started you should do the following : 
1. execute the command: `amplify add auth`
2. Enter the following when prompted:
````
? Do you want to use the default authentication and security configuration?
    `Default configuration`
? How do you want users to be able to sign in?
    `Username`
? Do you want to configure advanced settings?
    `No, I am done.`
````
3.  push your changes to the cloud using the command: `amplify push`  
`amplifyconfiguration.json` should be updated to reference provisioned backend auth resources.

4. Install Amplify Libraries : Add the following dependency to your app's build.gradle and then sync.
````
dependencies {
    implementation 'com.amplifyframework:aws-auth-cognito:1.35.4'
}
````

5. Initialize Amplify Auth : Add the Auth plugin before calling Amplify.configure .
````
// Add this line, to include the Auth plugin.
Amplify.addPlugin(new AWSCognitoAuthPlugin());
Amplify.configure(getApplicationContext());
````
6. Check the current auth session ,you can run this from your MainActivity's onCreate method.
````
Amplify.Auth.fetchAuthSession(
    result -> Log.i("AmplifyQuickstart", result.toString()),
    error -> Log.e("AmplifyQuickstart", error.toString())
);
````



## Sign in
***
After getting started you have to follow these steps to set up to use Amazon Cognito User Pools which manages the users and their properties: 
1.  Invoke the following api to initiate a sign up flow.
````
AuthSignUpOptions options = AuthSignUpOptions.builder()
    .userAttribute(AuthUserAttributeKey.email(), "my@email.com")
    .build();
Amplify.Auth.signUp("username", "Password123", options,
    result -> Log.i("AuthQuickStart", "Result: " + result.toString()),
    error -> Log.e("AuthQuickStart", "Sign up failed", error)
);
````

2.  confirm the user .
````
Amplify.Auth.confirmSignUp(
    "username",
    "the code you received via email",
    result -> Log.i("AuthQuickstart", result.isSignUpComplete() ? "Confirm signUp succeeded" : "Confirm sign up not complete"),
    error -> Log.e("AuthQuickstart", error.toString())
);
````
3. Implement a UI to get the username and password from the user then call the following method :
````
Amplify.Auth.signIn(
    "username",
    "password",
    result -> Log.i("AuthQuickstart", result.isSignInComplete() ? "Sign in succeeded" : "Sign in not complete"),
    error -> Log.e("AuthQuickstart", error.toString())
);
````
**You have now successfully registered a user and authenticated with that user's username and password with Amplify.**