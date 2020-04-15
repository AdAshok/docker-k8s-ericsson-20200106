kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0-rc7/aio/deploy/recommended.yaml

Kubectl get ns 

# kubectl  get svc -n kube rnetes-dashboard
NAME                        TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)         AGE
dashboard-metrics-scraper   ClusterIP   10.98.21.11    <none>        8000/TCP        26m
kubernetes-dashboard        NodePort    10.96.73.130   <none>        443:32627/TCP   26m

Note : Expose kubernetes-dashboard on NodePort. 

# cat sample-user.yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: admin-user-1
  namespace: kubernetes-dashboard
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: admin-user-1
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: cluster-admin
subjects:
- kind: ServiceAccount
  name: admin-user-1
  namespace: kubernetes-dashboard

# kubectl create -f sample -user.yaml


Grab the Token for Login: 

kubectl -n kubernetes-dashboard get secret | grep admin-user-1
kubectl -n kubernetes-dashboard describe secret admin-user-1-token-fb6bq

Now go & access the dashboard via URL


