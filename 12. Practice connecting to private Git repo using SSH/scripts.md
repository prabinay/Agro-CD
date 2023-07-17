## Add Private Git Repo
Create a private repo , (Skip this, if you already created the private repo):

Create an empty repo as private.
Click on import code
Paste this repo url https://github.com/mabusaa/argocd-example-apps
Define and create k8s secret in order to connect private git repo with Argo CD, use below specs and apply it using kubectl:

You can use the definition file /practice/repo.yaml

Name: private-repo-ssh
Url: Set the private repo Url (ssh format) git@github.com:YOUR_ACCOUNT/PRIVATE_REPO.git .
sshPrivateKey: generate key pairs and set the private key. Adding a new SSH key to your GitHub account
Create the secret using kubectl

`kubectl apply -f /practice/repo.yaml`

Verify secret is created

`kubectl get secret private-repo-ssh -n argocd`



## Verify Repo Status
Open Argo CD web and verify the repo status.
You need admin user password to login in web.

`kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo`
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
Source repo: Your_Private_Repo_Url_SSH_Format ex: git@github.com:YOUR_ACCOUNT/PRIVATE_REPO.git
Source path: guestbook
Source branch: master
Create the application using kubectl

`kubectl apply -f /practice/application.yaml`

Verify application is created

`kubectl get application -n argocd`

Sync the application to create the resources in destination cluster. ACCESS ARGO CD