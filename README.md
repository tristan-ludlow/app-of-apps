# The "app-of-apps" solution for k8s antispam setup

This project facilitates the "one-click" deployment of our entire antispam setup on Kubernetes, using the ArgoCD service.

### Quick example

```sh
argocd app create app-of-apps --repo https://github.com/tristan-ludlow/app-of-apps.git --path helm-chart --dest-namespace default --dest-server https://kubernetes.default.svc --helm-set env=dev --helm-set namespace=argocd
```

## The app-of-apps Helm chart

Contains the ArgoCD application manifests for all services we will need to deploy, saved as Helm templates. Its being a Helm chart, allows us to pass values to the app-of-apps such as env type, namespaces, project, etc...

## Custom values for external helm charts

Since some of the Apps we are using will be coming from third-party Helm chart repos, we will need to provide those with custom values. At this stage we have decided to store all of those in this same repo to avoid creating new repos for every such app containing only those files.
