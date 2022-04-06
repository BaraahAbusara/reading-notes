# Class-17 : Spring Authorization
***

In this file I will be summarizing what I have learnt in class-17 reading notes which included the following resources : 
- [Spring Boot and OAuth2](https://spring.io/guides/tutorials/spring-boot-oauth2/).

## Spring Boot and OAuth2
***
This guide shows us how to build an app doing various things with *social login* using OAuth 2.0 and Spring Boot.
This guid creats the application works as follows :
- **Single Sign On With GitHub :**  
 Yes, the authentication is going to be by signing in to gitHub. 
- **Creating a New Project : **  
This can be used in many ways such as using [https://start.spring.io](https://start.spring.io) or uing this command line : 
```
$ mkdir ui && cd ui
$ curl https://start.spring.io/starter.tgz -d style=web -d name=simple | tar -xzvf - 
```
- **Add a Home Page :**  
Create an `index.html` file in `src/main/resources/static` that is better to be linked to the styling sheet and javascript code.

- **Securing the Application with GitHub and Spring Security:**
Add Spring Security as a dependency ;
```
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-oauth2-client</artifactId>
</dependency>
```

- **configure your app to use GitHub as the authentication provider**  
  
- **Add a New GitHub App:**
    - Select "New OAuth App".
    - Register a new OAuth application.
    - indicate the Authorization callback URL as` http://localhost:8080/login/oauth2/code/github` and click Register Application.

- **Configure `application.yml`:**
    -  to make the link to GitHub, add the following to your application.yml:
    ````
    spring:
        security:
            oauth2:
                client:
                    registration:
                        github:
                            clientId: github-client-id
                            clientSecret: github-client-secret
# ...
    ````
- **Boot Up the Application**

Now we are reasy to make more features like:  
1. Add a Welcome Page that includes conditional content that appears for authenticated or unothenticated users. 
```
<div class="container unauthenticated">
    With GitHub: <a href="/oauth2/authorization/github">click here</a>
</div>
<div class="container authenticated" style="display:none">
    Logged in as: <span id="user"></span>
</div>
```
with the help of this java script code 
```
<script type="text/javascript">
    $.get("/user", function(data) {
        $("#user").html(data.name);
        $(".unauthenticated").hide()
        $(".authenticated").show()
    });
</script>
```

then Create The `/user` Endpoint.
and make SocialApplication class extends WebSecurityConfigurerAdapter , and uses @SpringBootApplication.

2. Add a Logout Button, a Logout Endpoint and Adding the CSRF Token in the Client.

3. Login with GitHub.  

4. Adding an Error Page for Unauthenticated Users.