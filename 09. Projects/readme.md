Practice creating an Argo CD project and allowing specific destinations , in this practice we will cover:

Define and create Argo CD Project declaratively with below info:
Allow all sources (repos).
Allow local cluster and namespace ns-1 only as destination.
Allow all cluster and namespace scoped resources.
Define and create and Argo CD Application that is using unpermitted namespace as destination, and verify that Argo CD deny this application.
Update the application with permitted namespace, and sync the application.