## Index 
0. [Project Definition](#0-Project-Definition)
1. [Architecture](#1-Architecture)
2. [How To Run](#2-How-To-Run)

# 0. Project Definition
As a user you can register for an account online. Once you have registered you should recieve a confirmation email which will give you a hyperlink to activate your account; allowing you to log in to the dashboard via the login page. This was created using Kubenetes, npm and nginx. All the images used for the deployments have been uploaded to a docker.io account

# 1. Architecture 

![Kubenetediagram](/Kubenetediagram(2).jpg)

From the diagram above we can see how each of the services communicate with each other as ClusterIP's, LoadBalancers and Pods. 

Servers run on port 3000.

Clients run on port 8080.

**Gateway**:
* This runs the nginx.conf file which gives the front and backend their ports. This is deployed as a load balancer due to needing access to an external ip address
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
 **Applications used**
 * Nodejs - Frontend
 * Vuejs - Frontend
 * MongoDB - Database 
 * Nginx.conf - Web Server

 **Setup**
 1. Create a kubenete cluster by opening gcloud console and writing gcloud container clusters name projectname --zone projectzone 
 
 2. Access kubenete cluster by typing gcloud container clusters get-credentials name projectname --zone projectzone
 
 3. Ensure the the kubenetes has enough nodes up and running by changing the amount of virtual machines. 
 
 4. Git clone project folder
 
 5. Deploy gateway service, deployment and conf-map.yaml file to get External IP address for step 5
 
 6. Change the IP in the authenticationservice-deployment file to the External IP of the gateway. 
 
 7. Deploy mongo-service service and deployment files 
 
 8. Repeat the step above for each of the file.  
 
 9. Once all the services and deployments are up and running go to http://gatewayexternalIP/authentication/register

gatewayeternalIP should appear when searching kubectl get service

This should get the project to work successfully. 


