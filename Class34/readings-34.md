# Class-34 : Monetization


In this file I will be summarizing what I have learnt in class-34 reading notes which included the following resources :
- [Google’s app publishing guide](https://developer.android.com/studio/publish)


## Google’s app publishing guide 
***
Publishing your appliation is the act of making the application able to be installed and used from other users , **but how can we do that?**   

### Prepare the application for release
Preparing your application for release is a multi-step process that involves the following tasks:

1. Configuring your application for release.
2. Building and signing a release version of your application.
3. Testing the release version of your application.
4. Updating application resources for release.

5. Preparing remote servers and services that your application depends on.

You may have to perform several other tasks as part of the preparation process. see [Preparing for Release](https://developer.android.com/studio/publish/preparing) in the Dev Guide.  
When you are finished preparing your application for release you will have a signed .apk file that you can distribute to users.
### Release the application to users
You can release your application to users in several ways such as : send it directly to a user release it in a/your website or you can release it through an application marketplace such as Google Play. 
but **How?**

#### Releasing through an app marketplace
##### Releasing your apps on Google Play
1. Preparing promotional materials.
2. Configuring options and uploading assets.
3. Publishing the release version of your application.
#### Releasing through a website
1. prepare your application for release in the normal way.
2. host the release-ready APK file on your website and provide a download link to users.

the installation process will start automatically only if the user has configured their Settings to allow the installation of apps from unknown sources  which has couple disadvantages,such as : 
1. You will not be able to use Google Play's In-app Billing service to sell in-app products.
2. You will not be able to use the Licensing service to help prevent unauthorized installation and use of your application.

#### User opt-in for unknown apps and sources
- On devices running Android 8.0 (API level 26) and higher :  users must navigate to the *Install unknown apps system settings* screen to *enable app installations from a particular source*.

- On devices running Android 7.1.1 (API level 25) and lower : users must either enable the *Unknown sources system setting* or allow a *single installation of an unknown app.*