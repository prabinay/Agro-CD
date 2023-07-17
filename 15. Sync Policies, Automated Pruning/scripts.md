## Create Argo CD Application
Create an Argo CD application declaratively using Yaml with below specs and apply it using kubectl:

You can use the definition file /practice/application.yaml

Name: auto-pruning-demo
Destination cluster url (local cluster): https://kubernetes.default.svc
Destination namespace: auto-pruning-demo
Source repo: https://github.com/mabusaa/argocd-example-apps.git , Fork the repo and set your repo url.
Source path: guestbook-with-sub-directories , (path of manifests where it include k8s service and deployment files).
Source branch: master
Create the application using kubectl

kubectl apply -f /practice/application.yaml

Verify application is created and synced

kubectl get application -n argocd

Verify that a service and deployment created in auto-pruning-demo namespace

kubectl get deploy,service -n auto-pruning-demo