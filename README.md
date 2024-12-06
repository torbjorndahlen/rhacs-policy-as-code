# rhacs-policy-as-code
Demo of RHACS Policy as Code feature

## Instructions

In RHACS Policy Management UI, clone the 30 Day Scan Age policy and disable it.
Save the copied policy as Custom Resource. The Policy will be labeled as Locally Managed.
Push the policy yaml file to a git repo.

In ArgoCD, create a new Application as follows:

Project: default
Cluster: https://kubernetes.default.svc
Namespace: stackrox
Git repo: https://github.com/torbjorndahlen/rhacs-policy-as-code
Path: policy

Optionally, set sync policy to Automated

To test the deployment of the policy, change the 'disabled' property in the policy CR.
Sync in ArgoCD.
In RHACS, the policy should have status enabled/disabled and the Origin should be changed to Externally Managed.

