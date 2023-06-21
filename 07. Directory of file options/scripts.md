Practice creating application that deploy a directory of Yaml files that exist in a git repo , in this practice we will cover:  

Declare an Argo CD application declaratively that deploy a directory of Yaml files.
Create the application using kubectl.
Sync the application and verify resources are created in cluster.
Update Argo CD application definition to include all files in all sub-directories using recursive option.
Re-sync the app.

## create app  
Create the application using kubectl

`kubectl apply -f /practice/directory-app.yaml`  

Verify application is created

`kubectl get application -n argocd`  

## Sync Application   
Open Argo CD web and sync the application.
You need admin user password to login in web.

`kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo`  
Then click on below link to open web UI, and login with admin user.

## Set recurse option  
Set recurse option in Argo CD application definition file /practice/application.yaml to include and deploy files in all sub-directories.  

Tip

Update the application using kubectl

`kubectl apply -f /practice/application.yaml`  

Verify the application is out of sync again

`kubectl get application -n argocd`  

## Re-sync the application  
Open Argo CD web and re-sync the application.
Click on below link to open web UI.  




