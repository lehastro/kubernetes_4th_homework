openssl genrsa -out deploy_view.key 2048

openssl req -new -key deploy_view.key \
  -out deploy_view.csr \
  -subj "/CN=deploy_view"
  
openssl x509 -req -in deploy_view.csr \
-CA ~/.minikube/ca.crt \
-CAkey ~/.minikube/ca.key \
-CAcreateserial \
-out deploy_view.crt -days 500

kubectl config set-credentials deploy_view \
--client-certificate=deploy_view.crt \
--client-key=deploy_view.key
  
  
kubectl config set-context deploy_view \
--cluster=minikube --user=deploy_view


nano ~/.kube/config 

 context:
    cluster: minikube
    user: deploy_view
  name: deploy_view

- name: deploy_view
  user:
    client-certificate: /home/aui/education/task_4/deploy_view.crt
    client-key: /home/aui/education/task_4/deploy_view.key
kubectl apply -f binding_deploy_view.yaml
    
    
    
    
    
openssl genrsa -out deploy_edit.key 2048

openssl req -new -key deploy_edit.key \
  -out deploy_edit.csr \
  -subj "/CN=deploy_edit"
  
openssl x509 -req -in deploy_edit.csr \
-CA ~/.minikube/ca.crt \
-CAkey ~/.minikube/ca.key \
-CAcreateserial \
-out deploy_edit.crt -days 500

kubectl config set-credentials deploy_edit \
--client-certificate=deploy_edit.crt \
--client-key=deploy_edit.key
  
  
kubectl config set-context deploy_edit \
--cluster=minikube --user=deploy_edit
kubectl apply -f binding_deploy_edit.yaml


nano ~/.kube/config 

 context:
    cluster: minikube
    user: deploy_edit
  name: deploy_edit

- name: deploy_edit
  user:
    client-certificate: /home/aui/education/task_4/deploy_edit.crt
    client-key: /home/aui/education/task_4/deploy_edit.key
    
    
    
    
kubectl create namespace prod


openssl genrsa -out prod_admin.key 2048

openssl req -new -key prod_admin.key \
  -out prod_admin.csr \
  -subj "/CN=prod_admin"
  
openssl x509 -req -in prod_admin.csr \
-CA ~/.minikube/ca.crt \
-CAkey ~/.minikube/ca.key \
-CAcreateserial \
-out prod_admin.crt -days 500

kubectl config set-credentials prod_admin \
--client-certificate=prod_admin.crt \
--client-key=prod_admin.key
  
  
kubectl config set-context prod_admin \
--cluster=minikube --user=prod_admin


nano ~/.kube/config 

 context:
    cluster: minikube
    user: prod_admin
  name: prod_admin

- name: prod_admin
  user:
    client-certificate: /home/aui/education/task_4/prod_admin.crt
    client-key: /home/aui/education/task_4/prod_admin.key
    
    
    
    
openssl genrsa -out prod_view.key 2048

openssl req -new -key prod_view.key \
  -out prod_view.csr \
  -subj "/CN=prod_view"
  
openssl x509 -req -in prod_view.csr \
-CA ~/.minikube/ca.crt \
-CAkey ~/.minikube/ca.key \
-CAcreateserial \
-out prod_view.crt -days 500

kubectl config set-credentials prod_view \
--client-certificate=prod_view.crt \
--client-key=prod_view.key
  
  
kubectl config set-context prod_view \
--cluster=minikube --user=prod_view


nano ~/.kube/config 

 context:
    cluster: minikube
    user: prod_view
  name: prod_view

- name: prod_view
  user:
    client-certificate: /home/aui/education/task_4/prod_view.crt
    client-key: /home/aui/education/task_4/prod_view.key




kubectl create serviceaccount sa-namespace-admin
kubectl describe sa sa-namespace-admin
kubectl describe secret sa-namespace-admin-token-2mrzt
kubectl config set-credentials sa-namespace-admin --token=eyJhbGciOiJSUzI1NiIsImtpZCI6ImNSeENDWkF1RHEwTmlaMUVtUTNreTM3MXdCeTV5c3h2b3VUTm5ucGx1N28ifQ.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJkZWZhdWx0Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZWNyZXQubmFtZSI6InNhLW5hbWVzcGFjZS1hZG1pbi10b2tlbi0ybXJ6dCIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VydmljZS1hY2NvdW50Lm5hbWUiOiJzYS1uYW1lc3BhY2UtYWRtaW4iLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlcnZpY2UtYWNjb3VudC51aWQiOiJhNDRjMTcxOS04NjEzLTQwMjQtODlmZC04YWQwNDY3MGFiMWYiLCJzdWIiOiJzeXN0ZW06c2VydmljZWFjY291bnQ6ZGVmYXVsdDpzYS1uYW1lc3BhY2UtYWRtaW4ifQ.XKSwSj8u6Ru0uTIYj3tNskGQmXlncFOON5sg7BNTNylEqJh4V86lLjEwTdIkKhbCnKXOz5kA4Z18j6RTAC7up51B5ozhZGxapIu0kXNkIQ2MOhEcc12t9wB72k_Q8ipTKJ1BKeBGmEJ3FIAkooUtgjnGlI8Rq6M_ndyX_zUvGf0C0ZTvyTJaX6pTQLJNKMr0qoLLNpPljtPgXRxWD6zVzzHAGvqVnBAetjqhK1FxTm0aJlJTYhThA8C6FOGAdPsC_3MTGq_ewhLOagSw1iJobU0raXEAs91jy9Bb2DXMre4pMtXrySafNghnjXect4GyqYkbI7bkoWJg669r9tpeOg
kubectl config set-context sa-namespace-admin --cluster=minikube --user=sa-namespace-admin
kubectl apply -f sa_binding.yaml
kubectl config use-context sa-namespace-admin
kubectl auth can-i create deployments --namespace default
    
    
    
    
    
    
 
    
    
    
 
  
