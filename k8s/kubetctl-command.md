### install hyperhit and minikube
`brew update`

`brew install hyperkit`

`brew install minikube`

`kubectl`

`minikube`

### create minikube cluster
`minikube start --vm-driver=hyperkit`

`kubectl get nodes`

`minikube status`

`kubectl version`

### delete cluster and restart in debug mode
`minikube delete`

`minikube start --vm-driver=hyperkit --v=7 --alsologtostderr`

`minikube status`

### kubectl commands
`kubectl get nodes`

`kubectl get pod`

`kubectl get services`

`kubectl create deployment nginx-depl --image=nginx`

`kubectl get deployment`

`kubectl get replicaset`

`kubectl edit deployment nginx-depl`

### debugging
`kubectl logs {pod-name}`

`kubectl exec -it {pod-name} -- bin/bash`

### create mongo deployment
`kubectl create deployment mongo-depl --image=mongo`

`kubectl logs mongo-depl-{pod-name}`

`kubectl describe pod mongo-depl-{pod-name}`

### delete deplyoment
`kubectl delete deployment mongo-depl`

`kubectl delete deployment nginx-depl`

### create or edit config file
`vim nginx-deployment.yaml`

`kubectl apply -f nginx-deployment.yaml`

`kubectl get pod`

`kubectl get deployment`

### delete with config
`kubectl delete -f nginx-deployment.yaml`

# Merge Kubernetes kubectl config files

###  Kubectl Config file(man page)
    Available Commands:
      current-context Display the current-context
      delete-cluster  Delete the specified cluster from the kubeconfig
      delete-context  Delete the specified context from the kubeconfig
      delete-user     Delete the specified user from the kubeconfig
      get-clusters    Display clusters defined in the kubeconfig
      get-contexts    Describe one or many contexts
      get-users       Display users defined in the kubeconfig
      rename-context  Rename a context from the kubeconfig file
      set             Set an individual value in a kubeconfig file
      set-cluster     Set a cluster entry in kubeconfig
      set-context     Set a context entry in kubeconfig
      set-credentials Set a user entry in kubeconfig
      unset           Unset an individual value in a kubeconfig file
      use-context     Set the current-context in a kubeconfig file
      view            Display merged kubeconfig settings or a specified kubeconfig file

### Make a copy of existing config files
```
$ cp ~/.kube/config ~/.kube/config.bak
```
### Merge the two config files together into a new config file as save it as a new file
```
$ KUBECONFIG=~/.kube/config:/path/to/new/config kubectl config view --flatten > /tmp/config
```
### Replace the old config file with the brand new merged config file from the previous step
```
$ mv /tmp/config ~/.kube/config
```
### Delete the backup after testing the merged config file(optional) 
```
$ rm 

