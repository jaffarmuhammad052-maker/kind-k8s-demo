Project Overview

This project demonstrates how to deploy and manage a simple web application in a lightweight Kubernetes cluster using Kind.
It covers:

Cluster setup and local development.

Deployments, Services, and ConfigMaps.

Observing self-healing and scaling.

Helm-based application deployment.

Container image management and monitoring.

This setup is ideal for beginner-to-advanced learning without overloading system resources.

Workflow (Sequential)

Cluster Setup

Install Kind, kubectl, and Docker.

Create a Kind cluster.

Verify cluster health and nodes.

Application Preparation

Prepare a simple web application (static HTML).

Build Docker image and load it into Kind.

Configuration Management

Create a ConfigMap for environment variables.

Inject the ConfigMap into the application deployment.

Deploying the Application

Deploy the application using a Kubernetes Deployment.

Expose the application via a Service (NodePort for external access).

Observe pods and services.

Helm Deployment (Optional)

Create a Helm chart for the application.

Use Helm to install, upgrade, and roll back deployments.

Observing the Cluster

Monitor pods, logs, and events.

Test self-healing by deleting pods.

Scale the application up or down.

Cleanup

Delete the Kind cluster and clean up Docker resources.

Sequential Commands with Descriptions
Step	Command	Description 
Install kubectl	kubectl version --client	                            Verify kubectl is installed.
Start cluster	kind create cluster --name kind-demo --wait 5m	        Create a local Kind Kubernetes cluster.
Check cluster	kubectl cluster-info	  

Show control plane endpoints.
List nodes	kubectl get nodes	Verify all nodes are ready.
Build Docker image	docker build -t kind-web:1.0 ./app	               Build application image.
Load image to Kind	kind load docker-image kind-web:1.0 --name kind-demo	Make the image available inside the Kind cluster.
Apply ConfigMap	kubectl apply -f k8s/configmap.yaml	Create configuration for the app.
Verify ConfigMap	kubectl get configmaps	List available ConfigMaps.
Deploy application	kubectl apply -f k8s/deployment.yaml	Deploy the application pods.
Expose service	kubectl apply -f k8s/service.yaml	Create Service for internal/external access.
View pods	kubectl get pods	Check pod status and health.
View services	kubectl get svc	Check Service endpoints and ports.
Scale deployment	kubectl scale deployment web-deployment --replicas=4	Increase or decrease replicas.
Observe self-healing	kubectl delete pod <pod-name>	Controller recreates deleted pods automatically.
View logs	kubectl logs <pod-name>	Inspect application logs.
Helm install	helm install my-app ./helm/my-app	Deploy application via Helm chart.
Helm upgrade	helm upgrade my-app ./helm/my-app	Update the deployed app.
Helm rollback	helm rollback my-app 1	Revert to previous Helm release.
Cleanup cluster	kind delete cluster --name kind-demo	Remove the local Kind cluster.
Cleanup Docker	docker system prune -f	Free unused Docker resources.
Key Learning Outcomes

Understand how Kind works and manage a lightweight Kubernetes cluster.

Deploy applications with Deployments and Services.

Use ConfigMaps for externalized configuration.

Observe self-healing and scaling behavior.

Deploy and manage apps with Helm charts.

Manage Docker images for Kubernetes.

Cleanly start, monitor, and remove a cluster.
