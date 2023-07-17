Add Private Git Repo
Create a private repo :  

Create an empty repo as private.
Click on import code
Paste this repo url https://github.com/mabusaa/argocd-example-apps
Define and create k8s secret in order to connect private git repo with Argo CD, use below specs and apply it using kubectl:  

You can use the definition file /practice/repo.yaml

Name: private-repo-https
Url: Set the private repo Url (https format) https://github.com/YOUR_ACCOUNT/YOUR_PRIVATE_REPO.git .
Password: generate a token from your github account and set it here.
Username: my-token  

Create the secret using kubectl

`kubectl apply -f /practice/repo.yaml`  


## Verify Repo Status
Open Argo CD web and verify the repo status.
You need admin user password to login in web.

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
Then click on below link to open web UI, and login with admin user.

ACCESS ARGO CD
  
Go to settings page.
Open repositories page.
Verify the repo status.  



## Create an Application

Create an Argo CD application declaratively that use the private repo as source of manifests, use below specs and apply it using kubectl:

You can use the definition file /practice/application.yaml

Name: app-1
Destination cluster url (local cluster): https://kubernetes.default.svc
Destination namespace: app-1
Source repo: Your_Private_Repo_Url_Https_Format ex: https://github.com/YOUR_ACCOUNT/YOUR_PRIVATE_REPO.git
Source path: guestbook
Source branch: master
Create the application using kubectl

`kubectl apply -f /practice/application.yaml`

Verify application is created

`kubectl get application -n argocd`




