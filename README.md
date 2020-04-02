# Kubernetes-Dashboard
Kubernetes Dashboard temp
Certificate issue resolve by 
 mkdir certs
 openssl req -nodes -newkey rsa:2048 -keyout certs/dashboard.key -out certs/dashboard.csr -subj "/C=/ST=/L=/O=/OU=/CN=kubernetes-dashboard"
 openssl x509 -req -sha256 -days 365 -in certs/dashboard.csr -signkey certs/dashboard.key -out certs/dashboard.crt
 kubectl create secret generic kubernetes-dashboard-certs --from-file=certs -n kubernetes-dashboard
 then deploy dashboard 
 kubectl apply -f dashboard.yml
 kubectl apply -f k8s-admin.yml
