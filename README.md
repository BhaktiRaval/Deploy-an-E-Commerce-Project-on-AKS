# Deploy-an-E-Commerce-Project-on-AKS
Deploy an E-Commerce Project on Azure Kubernetes Service

Create a resource group named 'ecommerce-demo'.
Kubernetes services -> Create Kubernetes cluster -> Kubernetes cluster name = 'three-tier'.
In cmd locate any particular path for project and run - 'git clone https://github.com/iam-veeramalla/three-tier-architecture-demo'.
cd three-tier-architecture-demo


Connect terminal to AKS cluster
Run below commands 
1. az aks get-credentials --resource-group ecommerce-demo --name three-tier
2. optional - kubectl get pods / kubectl config current-context (verify successful connection)
3. cd AKS -> cd helm
4. In readme file of helm can find out commands to run
5. kubectl create ns robot-shop
6. Get zip file from 'https://github.com/helm/helm/releases' and after extraction, place helm.exe file in 'C:\Windows\System32'.
7. helm install robot-shop --namespace robot-shop .
8. kubectl get pods -n robot-shop (verify all pods are running)
9. kubectl get svc -n robot-shop (web  LoadBalancer  10.0.60.42  48.216.184.204  8080:31283/TCP  12m --->>> get externalip and port then access app at that particular url ex: 48.216.184.204:8080)




To use ingress (benefits - web app firewall, host based routing etc ...)
Go to AKS cluster -> settings -> networking -> enable ingress controller
run -> kubectl apply -f ingress.yaml -n robot-shop
run -> kubectl get ing -n robot-shop (get address and access url)
NOTE : Application Gateway Ingress Controller addon is only available with Azure CNI Overlay in public preview.
