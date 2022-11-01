# devops-bootcamp-project-7
Demo project for Module 10 - Container orchestration w K8s

1. Install Minikube for local testing
brew install minikube

2. Start Minikube w Docker
minikube start --driver docker
minikube status

3. Create deployment w Kubectl
kubectl create deployment nginx-deployment --image=nginx
