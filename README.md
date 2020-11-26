# Jwt Springboot Reactjs Token Authentication Example - React.js Spring Security Login

Tutorial Link: https://loizenai.com/reactjs-springboot-jwt-token-authentication/

![Jwt-springboot-reactjs-token-authentication-example](https://loizenai.com/wp-content/uploads/2020/11/Reactjs-SpringBoot-Jwt-Token-Authentication-Example.png)

JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. And “How to build Reactjs Jwt SpringBoot Token Based Authentication Example?” is one of the most common questions for SpringBoot Java development world. So in the tutorial, I introduce how to implement an application “Reactjs JWT SpringBoot token Authentication Example” with details step by step and 100% running sourcecode.

– I give you an Epic of the application, a fullstack excutive flow from frontend to backend with overall architecture diagram.
– I give you a layer diagram of Reactjs JWT Application.
– I guide you detail-steps how to implement a security Jwt Token SpringBoot backend.
– I guide you step by step how to develop a Reactjs JWT Authentication application.
– Finally, I do an integrative testing from Reactjs JWT Authentication application to jwt SpringBoot Security RestAPIs.

## Overall System Architecture Diagram

![Overall System Architecture Diagram](https://loizenai.com/wp-content/uploads/2020/11/Reactjs-JWT-Authentication-Overall-Diagram-1.png)

For the Reactjs JWT Authentication tutorial, we have 2 projects:
– Backend project (using SpringBoot or Nodejs Express) provides secured RestAPIs with JWT token.
– Reactjs project will request RestAPIs from Backend system with the JWT Token Authentication implementation.

## JWT Authentication Sequence Diagram

The diagram below show how our system handles User Registration and User Login processes:

![JWT Authentication Sequence Diagram](https://loizenai.com/wp-content/uploads/2020/11/Reactjs-Jwt-Authentication-Working-Process-Diagram-1.png)

1. User Registration Phase:
– User uses a React.js register form to post user’s info (name, username, email, role, password) to Backend API /api/auth/signup.
– Backend will check the existing users in database and save user’s signup info to database. Finally, It will return a message (successfully or fail) to

2. User Login Phase:
– User posts user/password to signin to Backend RestAPI /api/auth/signin.
– Backend will check the username/password, if it is right, Backend will create and JWT string with secret then return it to Reactjs client.

After signin, user can request secured resources from backend server by adding the JWT token in Authorization Header. For each request, backend will check the JWT signature and then returns back the resources based on user’s registered authorities.

## Reactjs JWT Authentication Diagram Overview

Reactjs JWT Authentication would be built with 5 main kind blocks:

- Reactjs Router is a standard library for routing in React. It enables the navigation among views of various components in a React Application, allows changing the browser URL, and keeps the UI in sync with the URL.
- Reactjs Components let you split the UI into independent, reusable pieces, and think about each piece in isolation.
- Reactjs Service is a bridge between Reactjs Component and Backend Server, it is used to do technical logic with Backend Server (using Ajax Engine to fetch data from Backend, or using Local Storage to save user login data) and returned a response data to React.js Components
- Local Storage allow to save key/value pairs in a web browser. It is a place to save the login user’s info.
- Axios – (an Ajax Engine) is a promise-based HTTP client for the browser and Node. js. Axios makes it easy to send asynchronous HTTP requests to REST endpoints and perform CRUD operations.

## Jwt SpringBoot Token Security RestAPIs Diagram Overview
This is diagram for Spring Security/JWT (Springboot Token Based Authentication Example) classes that are separated into 3 layers:
– HTTP
– Spring Security
– REST API

![Jwt SpringBoot Token Security RestAPIs Diagram Overview](https://loizenai.com/wp-content/uploads/2020/11/Spring-Security-Jwt-Token-Authentication-Architecture-Diagram-1.png)

Look at the diagram above, we can easily associate these components with Spring Security Authentication process: receive HTTP request, filter, authenticate, store Authentication data, generate token, get User details, authorize, handle exception…

At a glance:
– SecurityContextHolder provides access to the SecurityContext.
– SecurityContext holds the Authentication and possibly request-specific security information.
– Authentication represents the principal which includes GrantedAuthority that reflects the application-wide permissions granted to a principal.
– UserDetails contains necessary information to build an Authentication object from DAOs or other source of security data.
– UserDetailsService helps to create a UserDetails from a String-based username and is usually used by AuthenticationProvider.
– JwtAuthTokenFilter (extends OncePerRequestFilter) pre-processes HTTP request, from Token, create Authentication and populate it to SecurityContext.
– JwtProvider validates, parses token String or generates token String from UserDetails.
– UsernamePasswordAuthenticationToken gets username/password from login Request and combines into an instance of Authentication interface.
– AuthenticationManager uses DaoAuthenticationProvider (with help of UserDetailsService & PasswordEncoder) to validate instance of UsernamePasswordAuthenticationToken, then returns a fully populated Authentication instance on successful authentication.
– SecurityContext is established by calling SecurityContextHolder.getContext().setAuthentication(…​) with returned authentication object above.
– AuthenticationEntryPoint handles AuthenticationException.
– Access to Restful API is protected by HTTPSecurity and authorized with Method Security Expressions.

## Project Goal

We create a Reactjs JWT Authentication project as below:

[Reactjs Project structure](https://loizenai.com/wp-content/uploads/2020/11/Reactjs-Jwt-Authentication-project-structure-1.png)

It includes 8 components and 2 services and a router in app.js file.

– Home page:

![Home Page](https://loizenai.com/wp-content/uploads/2020/11/Reactjs-Home-Page-3.png)

– User Register page:

![User Register page](https://loizenai.com/wp-content/uploads/2020/11/Reactjs-JWT-Authentication-Register-Form-Validation-1.png)

– Login Page:

![Login Page](https://loizenai.com/wp-content/uploads/2020/11/reactjs-jwt-authentication-wrong-login-user-validation-3.png)

– Profile Page:

![Profile Page](https://loizenai.com/wp-content/uploads/2020/11/Reactjs-jwt-authentication-sign-in-successfully-2.png)

– Use Page:

[User page](https://loizenai.com/wp-content/uploads/2020/11/Reactjs-jwt-authentication-User-Page-Content-3.png)

– Project Manager Page:

![Project Manager Page](https://loizenai.com/wp-content/uploads/2020/11/Reactjs-JWT-Authentication-PM-Content-2.png)

– Reactjs Admin page:

![Reactjs Admin page](https://loizenai.com/wp-content/uploads/2020/11/Reactjs-jwt-authentication-admin-page-3.png)

## Realated post

[Angular 10 + Spring Boot JWT Token Based Authentication Example – Spring Security + MySQL](https://loizenai.com/angular-10-spring-boot-jwt-token-based-authentication-example-spring-security-mysql-database/)
[Angular 10 + Nodejs JWT Token Based Authentication with MySQL Example – Express RestAPIs + JWT + BCryptjs + Sequelize](https://loizenai.com/angular-10-nodejs-jwt-authentication-mysql-examples-tutorials/)
[SpringBoot Token Based Authentication Example – MySQL + JWT+ Spring JPA + RestAPIs](https://loizenai.com/spring-boot-security-jwt-token-bsed-authentication-example-mysql-spring-jpa-restapis/)
