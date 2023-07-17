## Add Credential Template
Credential templates: used If you want to use the same credentials for multiple private repositories in your organization without having to repeat credential configuration.
Define and create k8s secret for credential templates, use below specs and apply it using kubectl:

You can use the definition file /practice/repo-creds.yaml

Name: repo-creds-https
Url: root repos url , example: https://github.com/ACCOUNT_NAME
Password: generate a token from your Github account and set it here.
Username: my-token
Create the secret using kubectl

`kubectl apply -f /practice/repo-creds.yaml`

Verify secret is created

`kubectl get secret repo-creds-https -n argocd`



## Verify Credential Template in Web
Open Argo CD web and verify the credential templates in repositories page.
You need admin user password to login in web.

`kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo`
Then click on below link to open web UI, and login with admin user.

ACCESS ARGO CD

Go to settings page.
Open repositories page.
Verify credential template is appearing in this page.


## Create an Application
Verify credential template is working by creating an Argo CD application that use a private repo within your account, use below specs and apply it using kubectl:

You can use the definition file /practice/application.yaml

Name: app-1
Destination cluster url (local cluster): https://kubernetes.default.svc
Destination namespace: app-1
Source repo: Your_Private_Repo_Url_Https_Format ex: https://github.com/YOUR_ACCOUNT/argocd-example-apps.git (assuming you forked https://github.com/mabusaa/argocd-example-apps.git )
Source path: guestbook
Source branch: master
Create the application using kubectl

`kubectl apply -f /practice/application.yaml`

Verify application is created

`kubectl get application -n argocd`

Sync the application to create the resources in destination cluster. ACCESS ARGO CD