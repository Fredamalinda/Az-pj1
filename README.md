# Az-pj1
Static HTML web app with Azure Cloud Shell
## Static HTML web app with Azure Cloud Shell
This lab comes from the Explore Azure App Service learning program on learn.mircosoft.com 
In this exercise, I'll be deploying a basic HTML+CSS site to Azure App Service by using the Azure CLI az webapp up command. Then update the code and redeploy it by using the same command.

The az webapp up command makes it easy to create and update web apps. When executed it performs the following actions:
- Create a default resource group if one isn't specified.
- Create a default app service plan.
- Create an app with the specified name.
- Zip deploy files from the current working directory to the web app.

### Steps
First I'm going to create a directory and navigate to it.
```
mkdir htmlapp

cd htmlapp
```

Then `git` the sample repo and put it in that directory. 
```
git clone https://github.com/Azure-Samples/html-docs-hello-world.git
```

Set variables to hold the resource group and app names by running the following commands.
```
resourceGroup=$(az group list --query "[].{id:name}" -o tsv)
appName=az204app$RANDOM
```

Now I will create the web app by changing to the directory that contains the sample code and run the `az webapp up` command.
```
cd html-docs-hello-world

az webapp up -g $resourceGroup -n $appName --html
```

It will look something like this:
![image](https://github.com/Fredamalinda/Az-pj1/assets/108156971/3c24fb9a-19df-41e6-abfa-3b7c84bb1376)


Use the URL in the output and open it in your browser (https://yourAppName.azurewebsites.net) to verify the app is running. - take note of the title at the top of the page. Leave the browser open on the app for the next section. This is how it should look:
![image](https://github.com/Fredamalinda/Az-pj1/assets/108156971/7c2539ab-b9d2-49b2-b992-fe4282017018)


Lets Update and Redeploy the app

In the Cloud Shell, type `code index.html` to open the editor. It will look like this:
![image](https://github.com/Fredamalinda/Az-pj1/assets/108156971/401cd7a2-1c09-4aa8-b15a-5c55813fcd35)

Go to the `<h1>` heading tag, and change the heading to whatever you want. I'm making mine "Fre's Static HTML Site using Azure".
![image](https://github.com/Fredamalinda/Az-pj1/assets/108156971/65a4ce62-0052-4c6c-b411-dab79fdbfbfb)

Use the commands ctrl-s to save and ctrl-q to exit.

Redeploy the app with the same `az webapp up` command you used earlier.
```
az webapp up -g $resourceGroup -n $appName --html
```

Then click the URL in the output and the changes will reflect 
![image](https://github.com/Fredamalinda/Az-pj1/assets/108156971/e12c5692-ad61-4286-9324-14a1e2fba737)















