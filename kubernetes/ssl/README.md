1. install cert-manager in kubernetes
   1. helm repo add jetstack https://charts.jetstack.io  
   2. helm repo update
   3. helm install cert-manager jetstack/cert-manager --namespace cert-manager --create-namespace --set installCRDs=true
   4. kubectl -n cert-manager get all (test cert-manager is installed)
2. create let's encrypt cert issuer
   1. kubectl apply -f ssl/cert-issuer.yaml
   2. kubectl describe clusterissuer lets-encrypt-cluster-issuer
3. configure ingress with tls
   1. kubectl apply -f ingress.yaml
4. issue certificate
   1. kubectl apply -f ssl/certificate.yaml
   2. kubectl describe certificate tradery-admin-app

   
Troubleshooting:

1. kubectl get certificate
2. kubectl describe certificate tradery-admin
3. kubectl describe certificaterequest tradery-nlb-admin-b9t55
4. kubectl describe order tradery-nlb-admin-b9t55-2353724536
5. kubectl describe challenge tradery-nlb-admin-b9t55-2353724536-1537846427
