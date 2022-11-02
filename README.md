# devops-bootcamp-project-7
Demo project for Module 10 - Container orchestration w K8s

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
![Capture d’écran 2022-11-02 à 16 07 42](https://user-images.githubusercontent.com/62488871/199526117-421487d0-9505-4f05-a7c1-24237756d242.png)


