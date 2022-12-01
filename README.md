# devops-bootcamp-project-7
Demo projects for Module 10 - Container orchestration w K8s

1. Install Minikube for local testing
brew install minikube

2. Start Minikube w Docker
minikube start --driver docker
minikube status

3. Create deployment config file for mongo
<img width="569" alt="Capture d’écran 2022-11-02 à 14 59 21" src="https://user-images.githubusercontent.com/62488871/199511009-6c757c41-d0ea-45e8-9fbb-dbf932f9a70d.png">

4. Create secret config file for mongo (note: need to encode base64 secret values, echo -n 'value' | base64)
<img width="434" alt="Capture d’écran 2022-11-02 à 15 10 47" src="https://user-images.githubusercontent.com/62488871/199511376-87eec606-b74b-4c04-9610-9a27d55d9c61.png">

5. Order matters: need to deploy secret before deployment so that deployment can read secret values correctly
<img width="286" alt="Capture d’écran 2022-11-02 à 15 18 29" src="https://user-images.githubusercontent.com/62488871/199513447-d2ee42c1-3b63-4de9-bafc-0d9c3a89690e.png">

6. Reference secrets in deployment file
<img width="563" alt="Capture d’écran 2022-11-02 à 15 20 45" src="https://user-images.githubusercontent.com/62488871/199514062-b769d9e1-bbaf-46e3-856b-f52246692ab6.png">

7. Create deployment using deployment config file
<img width="535" alt="Capture d’écran 2022-11-02 à 15 24 04" src="https://user-images.githubusercontent.com/62488871/199515537-c9d949c5-530a-48a8-a2c5-5182a671b3ea.png">
<img width="522" alt="Capture d’écran 2022-11-02 à 15 24 31" src="https://user-images.githubusercontent.com/62488871/199515593-72aa1353-8c8a-4f91-a980-ff6829a0883f.png">

8. Add internal service config to existing deployment config file for mongo
<img width="344" alt="Capture d’écran 2022-11-02 à 15 30 52" src="https://user-images.githubusercontent.com/62488871/199517953-17b84bf2-116b-4fb1-9ea8-0d39f4395a61.png">

9. Create service using deployment file
<img width="275" alt="Capture d’écran 2022-11-02 à 15 30 58" src="https://user-images.githubusercontent.com/62488871/199518312-9d480d26-746a-4d65-9022-66f0b037a781.png">
<img width="497" alt="Capture d’écran 2022-11-02 à 15 31 37" src="https://user-images.githubusercontent.com/62488871/199518390-5b05a5d6-6343-4be5-bf3b-e88f45ca1ede.png">

10. Create deployment config file for mongo-express
<img width="428" alt="Capture d’écran 2022-11-02 à 15 49 41" src="https://user-images.githubusercontent.com/62488871/199521552-7f32c92f-f75a-4807-ae8e-5d46ceeae1d4.png">

11. Create configMap config file for mongo-express
<img width="382" alt="Capture d’écran 2022-11-02 à 15 48 29" src="https://user-images.githubusercontent.com/62488871/199521251-bbfa6b3a-c843-4631-8a8c-254286a7bb48.png">

12. Reference configMap values in mongo-express deployment file
<img width="440" alt="Capture d’écran 2022-11-02 à 15 56 43" src="https://user-images.githubusercontent.com/62488871/199523481-068d7baf-7963-4d17-b7c8-c77da9794c09.png">

13. Create configMap then mongo-express deployment - order matters
<img width="449" alt="Capture d’écran 2022-11-02 à 15 57 20" src="https://user-images.githubusercontent.com/62488871/199523641-0bfaa20a-dec3-4c8f-9358-99773e5c59c2.png">

14. Add external service config in mongo-express deployment file
<img width="461" alt="Capture d’écran 2022-11-02 à 16 02 18" src="https://user-images.githubusercontent.com/62488871/199524832-0fbf8a02-a8fc-4b47-9544-c98dd6c85042.png">

15. Create external service
<img width="575" alt="Capture d’écran 2022-11-02 à 16 00 51" src="https://user-images.githubusercontent.com/62488871/199524646-16514304-e631-46cf-9e2a-965bbd5b5d1c.png">

16. Open running app in browser and check that data persists
<img width="596" alt="Capture d’écran 2022-11-02 à 16 05 47" src="https://user-images.githubusercontent.com/62488871/199525645-90cd1e77-6b16-4c91-86d5-be6b038bd956.png">

<img width="596" alt="Capture d’écran 2022-11-02 à 16 05 47" src="https://user-images.githubusercontent.com/62488871/199526457-8948218c-b052-4718-a3d0-8dabd2562499.png">

---------------

Use Helm chart to deploy operator for Prometheus

1. Install helm chart
  helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
  helm repo update
  helm install prometheus prometheus-community/kube-prometheus-stack
<img width="661" alt="Capture d’écran 2022-11-29 à 15 23 59" src="https://user-images.githubusercontent.com/62488871/204555038-216994b0-3920-4a2b-8c68-3c4354068604.png">

2. Make Grafana accessible via port forwarding
  check which port grafana service is listening on - kubectl logs prometheus-grafana-6fdd6868b4-hw7mk -c grafana
  <img width="664" alt="Capture d’écran 2022-11-29 à 15 46 21" src="https://user-images.githubusercontent.com/62488871/204560877-73442620-f4f9-4c9a-95d6-b94ac6587356.png">
  port-forward - kubectl port-forward deployment/prometheus-grafana 3000
  check grafan is accessible via browser on port 3000
  <img width="966" alt="Capture d’écran 2022-11-29 à 15 49 31" src="https://user-images.githubusercontent.com/62488871/204561204-29d5a962-f0bf-47c1-a95e-7ccb2f802d8e.png">
  
---------------

Deploy Microservices App

1. Create Deployment & Service Configurations for each microservice in config file

![Capture d’écran 2022-11-30 à 23 07 16](https://user-images.githubusercontent.com/62488871/204918598-2627dce9-8978-4c44-affb-7266d58dca3d.png)

 Considerations:
 - make sure that all microservices have the right connections using endpoints (service name + port)
 - make frontend microservice accessible from outside the cluster usign NodePort
 - mount volume into redis microservice (emptyDir is good use case here)
 
 
 2. Deploy Microservices into K8s cluster
 
  - create cluster on Linode 

![Capture d’écran 2022-12-01 à 00 27 57](https://user-images.githubusercontent.com/62488871/204933327-dfd6998c-2c62-4d23-9c90-c4ac48639092.png)

  - download kubeconfig file

  - set permissions of kubeconfig file to stricter ones

![Capture d’écran 2022-12-01 à 00 31 49](https://user-images.githubusercontent.com/62488871/204933289-0b3abf11-866c-42d3-a192-f7c39e9c1a57.png)

  - export KUBECONFIG variable to point to the file and check access to cluster

![Capture d’écran 2022-12-01 à 00 33 14](https://user-images.githubusercontent.com/62488871/204933256-d7583855-38f4-41ed-bb68-25a7d348c560.png)

  - create namespace

![Capture d’écran 2022-12-01 à 00 35 15](https://user-images.githubusercontent.com/62488871/204933222-9554f207-45bb-48bb-8e55-2534fa939f16.png)

  - deploy microservice app
 
![Capture d’écran 2022-12-01 à 00 41 58](https://user-images.githubusercontent.com/62488871/204933174-5aa3f573-7bf9-44f3-8a5f-509b7b0018c1.png)
![Capture d’écran 2022-12-01 à 00 45 27](https://user-images.githubusercontent.com/62488871/204933121-4f67cf22-6cd8-4df6-af88-8921e0983a11.png)

  - access microservices through the browser using node ip + nodePort 
 
 <img width="668" alt="Capture d’écran 2022-12-01 à 00 47 58" src="https://user-images.githubusercontent.com/62488871/204933070-9766473b-a366-4650-a0fc-89f245cbc95d.png">
 
 
 ---------------
 
 Create Helm Chart for Microservices
 
 1. helm create <chart_name>
 
 <img width="717" alt="Capture d’écran 2022-12-01 à 18 29 01" src="https://user-images.githubusercontent.com/62488871/205120671-cfb385be-f9db-4ad4-86f3-c37b735af243.png">
 
 2. create basic template files
 
 <img width="522" alt="Capture d’écran 2022-12-01 à 18 53 01" src="https://user-images.githubusercontent.com/62488871/205125219-6a0e30ac-fe4e-432c-9f94-d9b61305c1d3.png">
<img width="387" alt="Capture d’écran 2022-12-01 à 18 53 12" src="https://user-images.githubusercontent.com/62488871/205125225-75a20ebc-78ab-4b01-888a-5d77d212ba8d.png">

  3. Set Values

