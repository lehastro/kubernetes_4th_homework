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


nano ~/.kube/config \
 context: \
    cluster: minikube \
    user: deploy_view \
  name: deploy_view \

- name: deploy_view \
  user: \
    client-certificate: /home/aui/education/task_4/deploy_view.crt \
    client-key: /home/aui/education/task_4/deploy_view.key \
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



nano ~/.kube/config \ 

 context: \
    cluster: minikube \
    user: deploy_edit \
  name: deploy_edit \

- name: deploy_edit \
  user: \
    client-certificate: /home/aui/education/task_4/deploy_edit.crt \
    client-key: /home/aui/education/task_4/deploy_edit.key \
kubectl apply -f binding_deploy_edit.yaml  
    
    
    
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


nano ~/.kube/config \

 context: \
    cluster: minikube \
    user: prod_admin \
  name: prod_admin \

- name: prod_admin \
  user: \
    client-certificate: /home/aui/education/task_4/prod_admin.crt \
    client-key: /home/aui/education/task_4/prod_admin.key 
    
    
 kubectl apply -f binding_prod_admin.yaml
    
    
    
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

 context: \
    cluster: minikube \
    user: prod_view \
  name: prod_view 
  
  
- name: prod_view \
  user: \
    client-certificate: /home/aui/education/task_4/prod_view.crt \
    client-key: /home/aui/education/task_4/prod_view.key 
   
 kubectl apply -f binding_prod_view.yaml




kubectl create serviceaccount sa-namespace-admin

kubectl describe sa sa-namespace-admin

kubectl describe secret sa-namespace-admin-token-2mrzt

kubectl config set-credentials sa-namespace-admin --token=<mytoken>
  
kubectl config set-context sa-namespace-admin --cluster=minikube --user=sa-namespace-admin
  
kubectl apply -f sa_binding.yaml
  
kubectl config use-context sa-namespace-admin
  
kubectl auth can-i create deployments --namespace default
    
    
    
    
    
    
 
    
    
    
 
  
