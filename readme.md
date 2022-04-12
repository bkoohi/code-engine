### Code Engine Labs

The objective of these labs are to demonstrate how to deploy sample application using IBM Cloud serverless sercvice, Code Engine. Ther are few labs in this excercie for deployment demonstration purposes:

     Deploy a hello world container application in Code Engine 
    
Additional IBM Cloud solution tutotials can be access from this link:
https://cloud.ibm.com/docs/solution-tutorials?topic=solution-tutorials-scalable-webapp-kubernetes

## Lab preparation 
If your userid and environment have not been setup already for these labs then follow these instructions for the setup of the initial Lab environment.

1- Create an access group in your IBM Cloud account: "Demo LABs"
https://cloud.ibm.com/iam/groups
Create
Enter "Demo LABs" as name of access group
Enter a short description
Add the following access polices:
	
1.1 VPC Infrastructure Services service
1.2 Cloud Object Storage service
1.3 Security Advisor service
1.4 All resource group
    resourceType string equals resource-group
1.5 Toolchain service
1.6 Certificate Manager service
1.7 Schematics service
1.8 All resources in account (including future IAM enabled services)

2- Create a resource group "labs"
https://cloud.ibm.com/account/resource-groups

3- Invite users to "Demo LABs" access group via:
https://cloud.ibm.com/iam/users/invite_users
enter user's email address
select "Demo LABs"

Users need to go to their notification section to accept the invite:
https://cloud.ibm.com/notifications
First time users of ibm cloud need to create a new ibm cloud id. Consult with your ibm contact for first time ID creation ( https://cloud.ibm.com/registration ) 

This tutorial requires:

    -IBM Cloud CLI - This CLI tool will enable you to interact with IBM Cloud.
        code-engine/ce plugin (code-engine/ce) - Plugins extend the capabilities of the IBM Cloud CLI with commands specific to a service. The Code      Engine plugin will give you access to Code Engine commands on IBM Cloud.
    -Optional Container Registry plugin (container-registry)
    -git to clone source code repository.
    -Optional, if you want to test running the app locally you will need to install Node.js.

For IBM Cloud CLI plugins setup, please follow these instructions: https://cloud.ibm.com/docs/solution-tutorials?topic=solution-tutorials-tutorials

### Lab 1- Deploy Hello World sample app 
The objective of this lab is to deploy a simple hello world http container app on-demand in code engine. 
In traditional container app deployment, there is a need to deploy an IKS or RedHat Kubernetes cluster to host a container app. Using code engine services in IBM Cloud, container app could run on demand upon application access request by users.

     Deploy a hello world container application in Code Engine servessless service in IBM Cloud.



1.1 Login in IBM Cloud and access the code engine service:
```
https://cloud.ibm.com/codeengine/overview
```

1.2 In "Run a container image" section, select start creating

1.3 Under "Select a project", select "Create Project"

    * In right hand pannel, under Location , set it to Dallas
    
    * enter a project name "<your-initial>-hello-world" then select "Create".
    
    * under Runtime Setting, set "Min number of instances" to 1.
    
    It takes a minute to create the new project and then select your project from the menu

1.4 Keep all other configuration with their default values and select Create on the right hand side pannel

1.5 It takes few minutes to deploy the new project. To access and view the status go to:
https://cloud.ibm.com/codeengine/projects

1.6. In Projects tab, select your project "<your_initial>-hello-world" from the list.

1.7 Select Applications tab in the left hand side pannel, it would display a list of applications deployed in the project. 

1.8 Select "Open URL" for helloworld* application, it would open a browser with hello application content.
```
Hello World from:
. ___  __  ____  ____
./ __)/  \(    \(  __)
( (__(  O )) D ( ) _)
.\___)\__/(____/(____)
.____  __ _   ___  __  __ _  ____
(  __)(  ( \ / __)(  )(  ( \(  __)
.) _) /    /( (_ \ )( /    / ) _)
(____)\_)__) \___/(__)\_)__)(____)

Some Env Vars:
--------------
CE_APP=helloworld-application-c6
CE_DOMAIN=us-south.codeengine.appdomain.cloud
CE_SUBDOMAIN=mpz7lrvm9l6
HOME=/root
HOSTNAME=helloworld-application-c6-00001-deployment-5969895685-x6ccb
K_REVISION=helloworld-application-c6-00001
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
PORT=8080
PWD=/
SHLVL=1
z=Set env var 'SHOW' to see all variables
```

1.9 In order to delete the project, go to list of code-engine projects
https://cloud.ibm.com/codeengine/projects

1.10 Select <your-initial>-hello-world app and then select Delete
   Enter your project name in the pannel and select Delete
   
1.11 Delete projects will stay in the backend system for 7 days and the same project name cannot be reused. If there is a need to reuse the same project name then you need to reclaim the project under "Project reclamations"
   
	
### Lab 2- Deploy a node.js app in Code Engine

	This tutorial walks you through the creation of a web application using the popular MEAN stack. It is composed of a MongoDB, Express web framework, Angular front end framework and a Node.js runtime. You will learn how to run a MEAN starter locally, create and use a managed database-as-a-service (DBasS), deploy the app to IBM Cloud and scale both the runtime and database resources.
Objectives

    Create and run a starter Node.js app locally.
    Create a managed Databases for MongoDB instance.
    Deploy the Node.js app to the cloud using Code Engine.
    Scale runtime CPU and memory resources.
    Scale database memory and disk resources.

Architecture diagram
	

![plot](https://cloud.ibm.com/docs-content/v1/content/18424ca4c7a916f2e2389b4fb009e891bdb76ff6/solution-tutorials/images/solution7/Architecture.png)
	
Pleae follow these lab instructions: https://cloud.ibm.com/docs/solution-tutorials?topic=solution-tutorials-mean-stack
	
### Lab 3- Build and deploy a sample app 
The objective of this lab is to build a container image locally and then deploy it in code engine. 

     Deploy a container application image and then deploy it in Code Engine.

Lab Preparation
	- Install Docker or Podman these instructions https://podman.io/getting-started/installation

3.1 Complete Step 1 & 2 from previous Node.js lab

	https://cloud.ibm.com/docs/solution-tutorials?topic=solution-tutorials-mean-stack
	
3.2  Build the container image:
```
 podman build . -t mean-stack:v1.0.0
```	

3.3 Test running container image locally:
```
 docker run -p 8080:8080 --env-file .env -ti mean-stack:v1.0.0 
```
Output:	
```
> mean-boilerplate-ibm-cloud@1.1.0 start
> node server.js

Connecting to database located at mongodb://ibm_cloud_608ef153_4be1_42ae_a541_fadc7b23f92f:ce2db9779a26d3261e0503d3d7233b008d5fb6f0408f419e4c7954fca67eb2b3@d04258d0-fdd3-40a5-8e3c-958d8fd90f8e-0.c0v4phir0ah9ul9trho0.databases.appdomain.cloud:30922,d04258d0-fdd3-40a5-8e3c-958d8fd90f8e-1.c0v4phir0ah9ul9trho0.databases.appdomain.cloud:30922,d04258d0-fdd3-40a5-8e3c-958d8fd90f8e-2.c0v4phir0ah9ul9trho0.databases.appdomain.cloud:30922/ibmclouddb?authSource=admin&replicaSet=replset...
Connected to database.
Configuring passport authentication...
Setting up app middleware...
Setting up app routes...
Application running at http://localhost:8080
```
3.4 Open up app link ( http://localhost:8080 ) in your browser:

Output

![plot](https://github.com/bkoohi/code-engine/blob/main/images/Screen%20Shot%202022-04-12%20at%205.20.54%20PM.png)
	
3.5 Login in Container registery
```
ibmcloud cr region-set global
```
output:
```
The region is set to 'global', the registry is 'icr.io'.

OK
```
For additional help on setting Container registery, please see https://cloud.ibm.com/registry/start
	
3.6 Create a name space for code-engine
```
ibmcloud cr namespace-add code-engine-space
```

3.7 Tag the image with your container registry's namespace/repository name.
```
podman tag mean-stack:v1.0.0 icr.io/code-engine-space/mean-stack
	
```

3.8 Push the image.
```
podman push icr.io/code-engine-space/mean-stack
```

3.9 List uploaded images to image repository

```
ibmcloud cr images
```
	
Output:	
```
% ibmcloud cr images                                              
Listing images...

Repository                            Tag      Digest         Namespace           Created      Size    Security status   
icr.io/code-engine-space/mean-stack   latest   25ace32e10a5   code-engine-space   1 hour ago   52 MB   No Issues   

OK
% 
``
3.10 Set the target resource group
```
ibmcloud target -g Default
```
	
3.11 - Create a Code Engine project
```
ibmcloud code-engine project create --name mean-stack
```
	
output:
```
Creating project 'mean-stack'...
ID for project 'mean-stack' is '877c5b39-cef5-4754-add5-df87411baf0e'.
Waiting for project 'mean-stack' to be active...
Now selecting project 'mean-stack'.
OK
```
3.12 Copy .env.example file to .env.
```
cp .env.example .env
```
	
3.13 Update .env file and add a hash value for encryption under:
```
SESSIO_SECRET
```

3.14 Update MONGDB_URL and CERTIFICATE_BASE64 varilable in .env file, run the below command:

```
ibmcloud resource service-key mean-starter-mongodb-key --output json
```
	
You can find the value required for MONGODB_URL under credentials -> connection -> mongodb -> composed and the value for CERTIFICATE_BASE64 under credentials -> connection -> mongodb -> certificate -> certificate_base64 in the returned JSON output.
	

3.15 Create a secret in the project that contains the keys/values from the .env file you used earlier to run the application locally, this secret will be consumed by the application running in the cloud. For more about secrets, see Setting up and using secrets and configmaps.
```
ibmcloud code-engine secret create --name mean-stack-secrets --from-env-file .env
```

3.16 Create the application based on the public container image that is based on the same source code downloaded from the https://github.com/IBM-Cloud/nodejs-MEAN-stack repository. If you are interested in the steps used to create this image, you can review create-container-image.md.

```
ibmcloud code-engine application create --name mean-stack-application --image icr.io/solution-tutorials/tutorial-mean-stack --env-from-secret mean-stack-secrets
```
