 Create the application using kubectl  

`kubectl apply -f /practice/application.yaml`   

Verify application is created  
`kubectl get application -n argocd`  



## Sync App
Open Argo CD web and sync the application.
You need admin user password to login in web.  

`kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo`
Then click on below link to open web UI, and login by admin user.

## Update helm release name

Update helm release name with value of my-release in Argo CD application definition file /practice/application.yaml


Tip

Update the application using kubectl

`kubectl apply -f /practice/application-update.yaml`  

Verify the application is out of sync again

`kubectl get application -n argocd` 

