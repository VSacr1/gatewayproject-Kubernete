## Index 
0. [Project Definition](#0-Project-Definition)
1. [Architecture](#1-Architecture)
2. [How To Run](#2-How-To-Run)

# 0. Project Definition
As a user you can register for an account online. Once you have registered you should recieve a confirmation email which will give you a hyperlink to activate your account; allowing you to log in to the dashboard via the login page. This was created using Kubenetes, npm and nginx. 

# 1. Architecture 

![Serverdiagram](/Serverdiagram.jpg)

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

 1. Create a kubenete cluster by opening gcloud console and writing gcloud container clusters name projectname --zone projectzone 
 2. Access kubenete cluster by typing gcloud container clusters get-credentials name projectname --zone projectzone
 3. Git clone project folder
 4. Deploy gateway service, deployment and conf-map.yaml file to get External IP address for step 5
 5. Change the IP in the authenticationservice-deployment file to the External IP of the gateway. 
 6. Deploy mongo-service service and deployment files 
 7. Repeat the step above for each of the file.  
 8. Once all the services and deployments are up and running go to http://gatewayexternalIP/authentication/register

gatewayeternalIP should appear when searching kubectl get service

This should get the project to work successfully. 


