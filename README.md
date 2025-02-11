# EKS

#### To connect to the cluster
``` 
aws sts get-caller-identity 
```

#### Update the kubeconfig file to grant user access to the cluster. Modify profile if you created a new user profile

#### If root User
``` 
aws eks update-kubeconfig --region <your region> --name <Name of cluster>
```


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

#### After applying the Loadbalancer Manifest, run the command to get the address
```
k get ingress -n cluster-service
```

#### To check if LB svc is up
```
kubectl get svc
curl -i <lb-address>:8080/about
```

#### To test if LB is working
```
curl -i --header "Host: <domain-name.com>" <ingress address>/about
```

#### After applying the Ingress Manifest, run the command to get the address
```
k get ingress -n ingress-test
```

#### To test if ingress is working
```
curl -i --header "Host: <domain-name.com>" <ingress address>/about
```

#### Use AWS certificate for TLS
