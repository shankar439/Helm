<h1 align="center"> Kubernetes </h1>
<h2 align="center"> Utilizing HELM essential commands </h2>

![imagegit](https://github.com/shankar439/Images/assets/70714976/3f46be90-a0a6-48e1-89e7-efc99734b989)

## What is HELM and it's advantages ?. 

  - `HELM is a package manager for Kubernetes, it simplifies the management and deployment of applications on Kubernetes. `
  - ### Advantages:
    - `Versioning and Rollbacks` - Helm provides versioning support, allowing you to roll back to previous versions of a release if an update causes issues.
    - `Reusability and Shareability` - Helm charts can be shared with the community, your team, or within your organization. This encourages code reuse and standardization across different projects and simplifies collaboration.
    - `Simplified Application Deployment` - Helm allows you to package your Kubernetes manifests into a single, versioned package called a "helm chart." This makes it easy to deploy complex applications in a single operation.

### prerequisite
  - Kubernetes cluster
  - Helm 
  
<br>
<br>



<h1 align="center">Lets Begin </h1>

- Commands going to be covered.

    - [helm install](https://helm.sh/docs/helm/helm_install/)
    - [helm upgrade](https://helm.sh/docs/helm/helm_upgrade/)
    - [helm rollback](https://helm.sh/docs/helm/helm_rollback/)
    - [helm uninstall](https://helm.sh/docs/helm/helm_uninstall/)
    - [helm ls](https://helm.sh/docs/helm/helm_list/)
    - [helm history](https://helm.sh/docs/helm/helm_history/)




<h2 align="center">helm install</h2>

- Throughout this tutorial I will use prometheus helm chart.

```
helm install [RELEASE_NAME] [CHART] [flags]
helm install prometheus prometheus/ -n monitoring
```

## Explanation

- `helm install` command is a fundamental Helm command that deploys a Kubernetes application using a Helm chart.
- We will pass three arguments first is the release name `prometheus` which is a like a primary name, which should be unique per namespace.
- Second is the actual path for the helm chart in my case I have it locally in my present working directory, so i use `prometheus/`.
- Third are some flags like `-n monitoring` is the namespace I wish the prometheus need to be installed.


<br>
<br>




<h2 align="center">helm upgrade</h2>

- The `helm upgrade` command is used to update an existing Kubernetes application deployment managed by Helm. This command is particularly useful when we want to deploy a new version of your application or change its configuration without uninstalling and re-installing the entire release.

```
helm upgrade [RELEASE_NAME] [CHART] [flags]
helm upgrade prometheus prometheus/ -n monitoring --atomic --cleanup-on-fail
```

## Explanation

- For this command too We will pass three arguments first is the release name `prometheus`, but this time we need to make sure to give the release name that we want to upgrade otherwise it will through an error release name not found like that.
- Second is the actual path for the helm chart exactly like what we did in install command.
- Third are some flags like `-n monitoring` is the namespace I wish the prometheus need to be installed. In addition to that please use these flags too `--atomic` this flag ensure if something goes wrong in installation process it will delete the the process and `--cleanup-on-fail` this flag will delete all the new resources created in this upgrade when upgrade fails.


<br>
<br>




<h2 align="center">helm rollback</h2>

- The `helm rollback` command in Helm is used to revert an application release to a previous version. It allows you to undo an upgrade or update to an earlier state, effectively rolling back the application to a known working configuration. This command is helpful when a new release introduces issues or unexpected behavior, and you need to quickly revert to a stable state.

```
helm rollback [RELEASE_NAME] [REVISION] [flags]
helm rollback prometheus 1 -n monitoring --atomic --cleanup-on-fail
```

## Explanation

- For this command too We will pass three arguments first is the release name `prometheus`.
- Second is the revision `1` which is basically the release of the helm charts we deployed. Using rollback command we can jump into any release we want, which is very useful in some conditions.
- Third are the flags which we used in upgrade command.


<br>
<br>




<h2 align="center">helm uninstall</h2>

- he `helm uninstall` command is used to remove a deployed application release and associated Kubernetes resources from a Kubernetes cluster. When you no longer need a specific application or want to clean up resources, you can use this command to delete the Helm-managed release and free up the resources used by the application.

```
helm uninstall [RELEASE_NAME] [flags]
helm uninstall prometheus -n monitoring
```

<br>
<br>



<h2 align="center">helm ls</h2>

- The `helm ls` command in Helm is used to list all the releases that have been deployed to a Kubernetes cluster using Helm. It provides an overview of the Helm-managed releases, showing important information about each release, such as the release name, version, chart used, status, and other relevant details.

```
helm ls [flags]
helm ls -n monitoring
helm ls -A
```

## Explanation

- The argument is the namespace I specifically want to check `-n monitoring`. And `-A` will list all from all namespace.
- This command will be useful to check the release name, while we want to perform upgrade command.

<br>
<br>




<h2 align="center">helm history</h2>

- The `helm history` command in Helm is used to view the revision history of a specific Helm release deployed in a Kubernetes cluster. It provides information about each revision, such as the revision number, using this command we will get the information about the revision which is used for rollback command to revert to exact release.

```
helm history [RELEASE_NAME]
helm history prometheus
```

<br>
<br>



## Conclusion

- We have seen what helm and its advantages.
- We performed some helm commands install, upgrade,  rollback, uninstall, ls, history.


<br>

# END