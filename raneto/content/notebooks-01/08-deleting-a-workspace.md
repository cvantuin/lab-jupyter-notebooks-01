---
Title: Deleting a Workspace
PrevPage: 07-mounting-via-webdav
NextPage: ../finish
ExitSign: Finish Workshop
---

The Jupyter Notebook workspace deployed using the `notebook-workspace` template is intended to serve as a long lived place where you can work on Jupyter notebooks. The use of attached persistent storage ensures that you will not loose your work even if the Jupyter Notebook application is restarted.

If you have finished with a particular Jupyter Notebook workspace, you can delete it, by deleting the resources created by the deployment.

To see a list of all the resources created, run:

```execute
oc get all,pvc --selector app=experiments -o name
```

This will display output similar to:

```
pod/experiments-3-62692
replicationcontroller/experiments-1
replicationcontroller/experiments-2
replicationcontroller/experiments-3
service/experiments
deploymentconfig.apps.openshift.io/experiments
route.route.openshift.io/experiments
route.route.openshift.io/experiments-webdav
persistentvolumeclaim/experiments-data
```

To then delete the Jupyter Notebook workspace, run:

```execute
oc delete all,pvc --selector app=experiments
```

Note that this command will delete the deployed application, as well as the persistent volume. If you wanted to retain the persistent volume in order to copy files out of it at a later time, do not include `pvc` in the list of resources to delete.
