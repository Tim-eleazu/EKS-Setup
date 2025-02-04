# EKS

#### To connect to the cluster
> ` aws sts get-caller-identity `

#### Update the kubeconfig file to gain access to the cluster
> ` aws eks update-kubeconfig --region <your region> --name <Name of cluster>`

#### Run commands to see you have access to the cluster
> ` kubectl get nodes`

> `kubectl auth can-i "*" "*"`

### For Cluster Role and CLuster Role Bindings use this YAML temp
> CLUSTER ROLE
```
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  name: viewer
rules:
  - apiGroups: ["*"]
    resources: ["deployments", "configmaps", "pods", "secrets", "services"]
    verbs: ["get", "list", "watch"]
```

> CLUSTER ROLE BINDING
```
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: my-viewer-binding
roleRef:
  kind: ClusterRole
  name: viewer
  apiGroup: rbac.authorization.k8s.io
subjects:
  - kind: Group
    name: my-viewer
    apiGroup: rbac.authorization.k8s.io
```