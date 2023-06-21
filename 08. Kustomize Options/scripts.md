# Kustomize Options

Practice creating application that deploy a kustomize application that exist in a git repo , in this practice we will cover:

Declare an Argo CD application declaratively that deploy a kustomize app.
Create the application using kubectl.
Sync the application and verify resources are created in cluster.
Update Argo CD application definition to reflect new name prefix and common label for all resources.
Re-sync the app  

## Create Argo CD Application  
Create an Argo CD application declaratively with below specs and apply it using kubectl:  
Create the application using kubectl

`kubectl apply -f /practice/kustomize-app.yaml`

Verify application is created

`kubectl get application -n argocd`  

## Sync the app

Open Argo CD web and sync the application.
You need admin user password to login in web.

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
Then click on below link to open web UI, and login with admin user.  


## Set name prefix and common label for all resources  
Set name prefix staging- and common label app: demo options in Argo CD application definition file /practice/application.yaml , this will update all resources with new name prefix and add a new common label.  


Tip

Update the application using kubectl

kubectl apply -f /practice/application.yaml

Verify the application is out of sync again

kubectl get application -n argocd  

## Re-sysnc the app



