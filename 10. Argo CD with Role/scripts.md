Create an Argo CD project declaratively with below specs and apply it using kubectl:

Create the project using kubectl

kubectl apply -f /practice/project.yaml

Verify project is created

kubectl get appproject -n argocd

## Create and Use Tokens

Create a token related to project using CLI, you have to use argocd proj role create-token command:

argocd proj role create-token PROJECT-NAME ROLE-NAME
`argocd proj role create-token project-with-role ci-role --grpc-web`  

We already created Argo CD application with name demo
Try to delete the application using the generated token, (deleting should be denied because the roles does not grant delete permission)

`argocd app delete demo --grpc-web --auth-token TOKEN_VALUE`  

Now, try to sync the application using the token, (this should work because role has the sync permission)

`argocd app sync demo --grpc-web --auth-token TOKEN_VALUE`  


