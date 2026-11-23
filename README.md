\# GitOps-Based Continuous Deployment Using Argo CD and Kubernetes



\## Project Overview



This project demonstrates GitOps-based continuous deployment using Kubernetes, Argo CD, GitHub, Docker and Minikube.



Argo CD continuously monitors a GitHub repository and automatically synchronizes Kubernetes resources with the desired configuration stored in Git.



The project demonstrates automated deployment, continuous synchronization, configuration drift detection and self-healing.



\## Technologies Used



\- Kubernetes

\- Minikube

\- Argo CD

\- Docker

\- Git and GitHub

\- NGINX

\- YAML

\- PowerShell



\## Architecture



Developer → GitHub Repository → Argo CD → Kubernetes Cluster → NGINX Application



Argo CD monitors the GitHub repository and reconciles the Kubernetes cluster whenever changes are pushed to the repository.



\## Project Structure



text argocd-gitops-demo/ │ ├── argocd/ │   └── application.yaml │ ├── k8s/ │   ├── configmap.yaml │   ├── deployment.yaml │   └── service.yaml │ ├── screenshots/ │   ├── 01-argocd-dashboard.png │   ├── 02-nginx-website.png │   ├── 03-initial-replicas.png │   ├── 04-manual-scaling-5.png │   └── 05-self-healing-2.png │ └── README.md 



\## Implementation



\### 1. Kubernetes Cluster Setup



Created a local Kubernetes cluster using Minikube with Docker as the driver.



\### 2. Argo CD Installation



Installed Argo CD in a dedicated Kubernetes namespace named argocd.



\### 3. GitHub Repository Integration



Connected Argo CD to the GitHub repository:



GitHub Repository



Configured Argo CD to monitor the main branch and the k8s directory.



\### 4. Kubernetes Application Deployment



Created and deployed the following Kubernetes resources:



\- ConfigMap: Stores the NGINX website HTML content.

\- Deployment: Runs two NGINX replicas.

\- Service: Exposes the NGINX application internally using ClusterIP.



\### 5. Automated Synchronization



Configured automated synchronization in Argo CD.



When changes are pushed to GitHub, Argo CD detects the updated desired state and synchronizes the Kubernetes resources automatically.



\### 6. Self-Healing Demonstration



Performed a configuration drift test:



1\. Initial deployment contained 2 NGINX replicas.

2\. Manually scaled the deployment to 5 replicas using kubectl.

3\. Argo CD detected the difference between the Git configuration and the live Kubernetes state.

4\. Argo CD automatically restored the deployment to 2 replicas.



This demonstrated configuration drift detection and automatic self-healing.



\### 7. Git-Based Application Update



Updated the NGINX website content through the GitHub repository.



Argo CD detected the repository changes and synchronized the updated ConfigMap with Kubernetes.



The website was subsequently restored to Version 1 through another GitHub update.



\## Argo CD Configuration



The Argo CD application is configured with:



\- Automated synchronization

\- Self-healing enabled

\- Automatic pruning enabled

\- Automatic namespace creation



\## Important Kubernetes Commands



\### Check Kubernetes Nodes



bash kubectl get nodes 



\### Check Argo CD Pods



bash kubectl get pods -n argocd 



\### Check Argo CD Application



bash kubectl get applications -n argocd 



\### Check Application Resources



bash kubectl get all -n gitops-demo 



\### Check Deployment



bash kubectl get deployment nginx-deployment -n gitops-demo 



\### Manually Scale Deployment



bash kubectl scale deployment nginx-deployment --replicas=5 -n gitops-demo 



\## Screenshots



\### Argo CD Dashboard



Argo CD Dashboard



\### NGINX Application



NGINX Website



\### Initial Deployment – 2 Replicas



Initial Replicas



\### Manual Scaling – 5 Replicas



Manual Scaling



\### Automatic Self-Healing – 2 Replicas



Self Healing



\## Project Outcomes



Successfully implemented a GitOps-based Kubernetes deployment workflow using Argo CD and GitHub.



Key achievements:



\- Automated Kubernetes deployment from GitHub.

\- Continuous synchronization of desired and live states.

\- Configuration drift detection.

\- Automatic self-healing and reconciliation.

\- Git-based application configuration management.

\- Deployment and management of NGINX using Kubernetes resources.



\## Repository



GitHub: https://github.com/bhuvanv71-creator/argocd-gitops-demo

