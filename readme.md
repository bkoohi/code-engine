### Code Engine Labs

The following tutorial labs will walks you through the creation of number of applications using IBM Cloud Code-engine service. Application

## 1- Hello world http app 
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

1.6. Once your project deployment completed access cloud shell
```
https://cloud.ibm.com/shell
```

1.7 Once shell started, set the resource group to Default
```
ibmcloud target -g Default
```

1.8 If your project deployed in us-east then set region in shell to proper region
```
ibmcloud target -r us-east
```

1.9 Select your project
```
ibmcloud ce project select -n "bk-hello world"
```

1.10 
