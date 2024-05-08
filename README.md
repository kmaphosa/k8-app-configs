# DevOps EPA Assessment Project

This project demonstrates the implementation of a DevOps pipeline, infrastructure-as-code principles, and continuous delivery using Kubernetes, ArgoCD, and Nginx. It also includes an observability stack for monitoring, logging, and alerting. The overall objective is to showcase a performant, secure, and highly available platform that meets the assessment criteria.

## Project Overview
### Key Features

- ArgoCD for Continuous Delivery: Automated deployment and synchronization of applications with GitOps principles.
- Kubernetes-Based Platform: Deployment of Nginx and WordPress services with Kubernetes manifests.
- Ingress Management: Centralized traffic routing with Nginx Ingress controllers.
- Observability Stack: Elasticsearch, Kibana, Metricbeat, and Filebeat for monitoring and alerting.
- CI/CD Integration: GitHub Actions or another CI/CD tool for automating builds and deployments.


## Getting Started

### Prerequisites

1. Kubernetes Cluster: Make sure you have access to a running Kubernetes cluster.
2. Kubectl: Kubernetes command-line tool installed.
3. ArgoCD: Installed and accessible.
4. GitHub Repository: Set up with this project's configuration.


### Installing

1. Clone the repository:
```
git clone https://github.com/kmaphosa/k8-app-configs.git
cd k8-app-configs/
```
2. Set up ArgoCD:
   - Apply the application.yaml file in the react-nginx directory to your ArgoCD instance.
3. Deploy the applications:
```
kubectl apply -f react-nginx/deployment.yaml
kubectl apply -f react-nginx/service.yaml
kubectl apply -f wordpress/mysql-deployment.yaml
kubectl apply -f wordpress/wordpress-deployment.yaml
```
4. Configure Ingress
```
kubectl apply -f elk-argocd-ingress.yaml
kubectl apply -f ingress.yaml

```
5. Configure Monitoring
```
helm install metricbeat -f monitoring/metricbeat-values.yaml elastic/metricbeat
helm install filebeat -f monitoring/filebeat-values.yaml elastic/filebeat

```
6. Access the Services:
- Ensure DNS or /etc/hosts entries point to the correct domains like elk.local and argocd.local.
- Access the services via the respective URLs:
  - Kibana: http://elk.local
  - ArgoCD: http://argocd.local

## Authors

keith.maphosa@baesystems.com  

