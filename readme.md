### Code Engine Labs

The objective of these labs are to demonstrate how to deploy sample application using IBM Cloud serverless sercvice, Code Engine. Ther are few labs in this excercie for deployment demonstration purposes:

     Deploy a hello world container application in Code Engine 
    


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



## Lab 1- Deploy Hello World sample app 
The objective of this lab is to deploy a simple hello world http container app on-demand in code engine. 
In traditional container app deployment, there is a need to deploy an IKS or RedHat Kubernetes cluster to host a container app. Using code engine services in IBM Cloud, container app could run on demand upon application access request by users.

     Deploy a hello world container application in Code Engine servessless service in IBM Cloud.

Additional IBM Cloud solution tutotials can be access from this link:
https://cloud.ibm.com/docs/solution-tutorials?topic=solution-tutorials-scalable-webapp-kubernetes

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
   
