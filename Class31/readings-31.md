# Class-31 : Espresso
***


In this file I will be summarizing what I have learnt in class-31 reading notes which included the following resources :
- [What Is AWS Amplify?](https://beabetterdev.com/2021/09/22/what-is-aws-amplify/)


## What Is AWS Amplify ?
 AWS Amplify is a toolchain that helps you build and deploy entire applications very quickly.
What is speacial about AWS Amplify is that Amplify offeres direct feature integration with AWS’ powerful backend services.
Following are Languages/platforms supported by AWS Amplify :
![ Languages/platforms supported by AWS Amplify](https://i0.wp.com/www.beabetterdev.com/wp-content/uploads/2021/09/image-27.png?resize=768%2C447&ssl=1)

Another special thing about AWS Amplify is that you can add functions to your appication without the need of knowing what was implemented behind the scenes such as :
- Storage 
- Authentication
- Monitoring
- PubSub functionalities
That way as a developer you will have more time to develop your own new functionalities to make your application better and more unique. 

In addition to that you can use **AWS CloudFormation**, which is an Infrastructure as Code service that allows you to define template files that instruct AWS which components you need for your application, and let AWS do the heavy lifting of provisioning those services.

## An Example Of Amplify Features :
Amplify is an abstraction that sits ontop of other core services, letting you quickly add functions without needing to understand which service is being used behind the scenes.
Following some of the  services AWS Amplify uses behind the scenes :

![The services AWS Amplify uses behind the scenes to offer its wide range of cloud integrated functions.](https://i0.wp.com/www.beabetterdev.com/wp-content/uploads/2021/09/image-28.png?resize=768%2C472&ssl=1)


## Usage 
To use AWS Amplify features you need to ineract with it through its CLI library which can be installed to the terminal. 
To create a new project,use `amplify configure` and `amplify init` command.
for adding an API use `amplify add api`
then you can create your application and finally run a deploy command to let everyone use your application. 