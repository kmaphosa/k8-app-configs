# Kubenetes CI/CD Project

This project demonstrates the implementation of a DevOps pipeline, infrastructure-as-code principles, and continuous delivery using Kubernetes, ArgoCD, and Nginx. It also includes an observability stack for monitoring, logging, and alerting.

## Project Overview
### Key Features

- CI/CD Pipeline with GitHub Actions**: Automated builds, testing, and deployment using GitHub Actions.
- Kubernetes-Based Platform (EKS)**: Deployment of Nginx and WordPress services with Kubernetes manifests.
- Ingress Management: Centralised traffic routing with Nginx Ingress controllers.
- Observability Stack: Prometheus and Grafana for monitoring and alerting.
- Docker: Containerisation of applications for consistent deployment.


## Getting Started

### Prerequisites


- AWS Account
- AWS CLI
- `eksctl`
- Docker
- GitHub account


### Setup instructions

1. Clone the repository:
```
git clone https://github.com/kmaphosa/k8-app-configs.git
cd k8-app-configs/

```
2. AWS Cloud environment:
```
- **Create IAM User**: Create an IAM user with programmatic access and attach the necessary policies for EKS and EC2.
- **Install AWS CLI**:
  ```sh
  curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"
  sudo installer -pkg AWSCLIV2.pkg -target /
  aws configure

```
3. Install eksctl
```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_$(uname -m).tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin

```
4. Create cluster
```
eksctl create cluster --name <cluster_name> --version 1.30 --region <region-code> --nodegroup-name <nodegroup_name> --node-type t3.medium --nodes 3 --nodes-min 1 --nodes-max 4 --managed

```
5. Configure and Run the pipeline:
- Update the following config files with your environment variables (.github/workflows/deploy.yml, k8s/prometheus-configmap.yaml, k8s/grafana-datasource-configmap.yaml)
- Access the services via the respective URLs:
```
kubectl port-forward -n monitoring svc/prometheus-kube-prometheus-prometheus 9090:9090
kubectl port-forward -n monitoring svc/grafana 3000:3000

```
  - Grafana: [http://localhost:3000]

## Authors

Keith Maphosa  

