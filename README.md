# EKS

#### To connect to the cluster
``` 
aws sts get-caller-identity 
```

#### Update the kubeconfig file to grant user access to the cluster
``` 
aws eks update-kubeconfig --region <your region> --name <Name of cluster> --profile <name of profile>
```

#### Run commands to see you have access to the cluster
``` 
kubectl get nodes 
```

``` 
kubectl auth can-i "*" "*" 
```
