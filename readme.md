### Code Engine Labs

The following tutorial labs will walks you through the creation of number of applications using IBM Cloud Code-engine service. Application

## 1- Deploy Hello World sample app 
The objective of this lab is to deploy a simple hello world http container app on-demand in code engine. 
In traditional container app deployment, there is a need to deploy an IKS or RedHat Kubernetes cluster to host a container app. Using code engine services in
IBM Cloud, container app could run on demain upon access by users.

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

## 2- Delete Hello World sample app 

2.1 Go to list of code-engine projects
https://cloud.ibm.com/codeengine/projects

2.2 Select <your-initial>-hello-world app and then select Delete
   Enter your project name in the pannel and select Delete
   
3.3 Delete projects will stay in the backend system for 7 days and the same project name cannot be reused. If there is a need to reuse the same project name then you need to reclaim the project under "Project reclamations"
   
