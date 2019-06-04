## Index 
0. [Project Definition](#0-Project-Definition)
1. [Architecture](#1-Architecture)
2. [How To Run](#2-How-To-Run)

# 0. Project Definition
As a user you can register for an account online. Once you have registered you should recieve a confirmation email which will give you a hyperlink to activate your account; allowing you to log in to the dashboard via the login page. This was created using Docker-compose, npm and nginx. 

# 1. Architecture 

![Server diagram](/Server diagram.xml)

From the diagram above we can see how each of the docker files communicate with each other. 

**Gateway**:
* This runs the nginx.conf file which gives the front and backend their ports 
* *Depends on Authentication service, Authentication client Dashboard client*

**Dashboard client** 
*

**Authentication client** 
* 

**Role Service**
*

**Group Service**
*

**Aes Encryption Service**
* 

**Authentication Service**: 
* This sends the activation link to the users email. 
* *Depends on Account Service, Email Service, Session-token-service* 

**Session Encryption Token**
*
* *Depends on: Aes-Encryption Service, Mongo Service*

**Account Service**: 
* *Depends on: Secret Service, Mongo Service*

**Secret Service**: 
* *Depends on: Mongo-Service*

**Mongo Service**
* This is responsible for running and maintaining the mongo database. 
* *Depends on: Mongo*

**Mongo**
* This communicates to the Mongo database

# 2. How To Run
 * Nodejs 
 * Vuejs
 * MongoDB
 * Nginx.conf

 1. Make a new google cloud virtual machine and git clone this project. 
 2. Change the .env file IP address to the ip of the virtual machine
 3. Enter the folder with the cd command and run docker-compose -d up. This will build and compile all the docker files inside this folder. 
 4. Once that is all running head to http://localhost/authentication/login

This should get the project to work successfully. 

Localhost = the ip of the virtual machine
