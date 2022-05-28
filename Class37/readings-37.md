# Class-37 : S3


In this file I will be summarizing what I have learnt in class-37 reading notes which included the following resources :
- [Introduction to Amazon S3 ](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html).
- [S3 with Amplify ](https://docs.amplify.aws/lib/storage/getting-started/q/platform/android/).


## Introduction to Amazon S3
***
### What is Amazon S3?
Amazon S3 is **Amazon Simple Storage Service** which is an object storage service that offers industry-leading scalability, data availability, security, and performance.

### Features of Amazon S3
1. Storage classes
2. Storage management
3. Access management
4. Data processing
5. Storage logging and monitoring
6. Analytics and insights
7. Strong consistency
### How Amazon S3 works
Amazon S3 is an object storage service that stores data as objects within buckets. An object is a file and any metadata that describes the file. A bucket is a container for objects.

### Amazon S3 data consistency model
Using Amazon S3 you will be able to read-after-write consistency for PUT, DELETE and GET requests of objects in your Amazon S3 bucket in all AWS Regions.   
Updates to a single key are **atomic**. For example, if you make a PUT request to an existing key from one thread and perform a GET request on the same key from a second thread concurrently, you will get either the old data or the new data, but never partial or corrupt data.

### Related services
After you load your data into Amazon S3, you can use it with other AWS services. The following are the services that you might use most frequently:  
- Amazon Elastic Compute Cloud (Amazon EC2) 
- Amazon EMR
- AWS Snow Family
- AWS Transfer Family 


### Accessing Amazon S3
You can work with Amazon S3 in any of the following ways:
1. AWS Management Console :   
If you've signed up for an AWS account, you can access the Amazon S3 console by signing into the AWS Management Console and choosing S3 from the AWS Management Console home page.
2. AWS Command Line Interface :  
check [ AWS Command Line Interface User Guide](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html)
3. AWS SDKs :   
The AWS SDKs provide a convenient way to create programmatic access to S3 and AWS. Amazon S3 is a REST service. You can send requests to Amazon S3 using the AWS SDK libraries. which wrap the underlying Amazon S3 REST API and simplify your programming tasks. 
4. Amazon S3 REST API:   
You can access S3 and AWS programmatically by using the Amazon S3 REST API. The REST API is an HTTP interface to Amazon S3. With the REST API, you use standard HTTP requests to create, fetch, and delete buckets and objects.
### Paying for Amazon S3
When you sign up for AWS, your AWS account is automatically signed up for all services in AWS, including Amazon S3. However, you are charged only for the services that you use.

## S3 with Amplify 
*** 
To setup and configure your application with Amplify Storage and go through following steps : 
1. execute the command: `amplify add storage`
2. push your changes to the cloud using the command: `amplify push`
3. Install Amplify Libraries to `build.gradle (Module: app)` in the `dependencies` block: 
````
dependencies {
    implementation 'com.amplifyframework:aws-storage-s3:1.35.4'
    implementation 'com.amplifyframework:aws-auth-cognito:1.35.4'
}
````
and then Click **Sync Now**.
4. Initialize Amplify Storage by : 
    -  call `Amplify.addPlugin()` method for each category.
    - call `Amplify.configure()` to complete initialization.
    - Add the following code to your `onCreate()` method :  

    Amplify.addPlugin(new AWSCognitoAuthPlugin());
    Amplify.addPlugin(new AWSS3StoragePlugin());    


**Note** that because the storage category requires auth, you will need to either configure guest access or sign in a user before using features in the storage category.

5. Uploading data to your bucket : specify the key and the data object to be uploaded : 

```
private void uploadFile() {
    File exampleFile = new File(getApplicationContext().getFilesDir(), "ExampleKey");

    try {
        BufferedWriter writer = new BufferedWriter(new FileWriter(exampleFile));
        writer.append("Example file contents");
        writer.close();
    } catch (Exception exception) {
        Log.e("MyAmplifyApp", "Upload failed", exception);
    }

    Amplify.Storage.uploadFile(
            "ExampleKey",
            exampleFile,
            result -> Log.i("MyAmplifyApp", "Successfully uploaded: " + result.getKey()),
            storageFailure -> Log.e("MyAmplifyApp", "Upload failed", storageFailure)
    );
}
```
you should see a new folder in your bucket, called `public`. It should contain a file called `ExampleKey`, whose contents is `Example file contents`.
    