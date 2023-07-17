Practice creating application with auto pruning enabled, so any resource deleted in git will be deleted in destination cluster, in this practice we will cover:

Define an Argo CD application and enable the automated sync only.
Apply the application using kubectl and verify that its synced directly.
Delete a resource from git repo and notice that its not deleted from destination cluster.
Then, enable the auto pruning in application definition and verify the service is deleted from destination cluster.