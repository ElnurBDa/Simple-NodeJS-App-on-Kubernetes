# Node.js Hello App on Kubernetes

This is a simple Node.js application that returns a `"Hello, <name>!"` message when a name is supplied as a query parameter. The app is deployed using Kubernetes.

## Prerequisites

- Docker
- Kubernetes (Minikube, EKS, GKE, etc.)
- kubectl (Kubernetes command-line tool)
- Node.js (for development)

## Setup

### 1. Clone the Repository

```bash
git clone https://github.com/ElnurBDa/Simple-NodeJS-App-on-Kubernetes
cd Simple-NodeJS-App-on-Kubernetes
```

### 2. Dockerize the Application

This Node.js application is containerized using Docker.

#### Build the Docker Image

Make sure Docker is installed, then run the following command to build the image:

```bash
docker build -t elnurbda/node-app:latest .
```

#### Push the Docker Image to Docker Hub

Push the built image to Docker Hub:

```bash
docker push elnurbda/node-app:latest
```

### 3. Kubernetes Deployment

#### Create Kubernetes Deployment

Ensure you have a Kubernetes cluster running (e.g., Minikube or a cloud provider). Apply the Kubernetes configuration files:

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

#### Check the Deployment and Service

Verify that the deployment and service are created:

```bash
kubectl get pods
kubectl get services
```

### 4. Access the Application

If using a `LoadBalancer` type service, find the external IP:

```bash
kubectl get svc node-app-service
```

Visit the following URL:

```
http://<external-ip>/hello?name=YourName
```

You should see the message: `Hello, YourName!`

### 5. Cleanup

To delete the deployment and service:

```bash
kubectl delete -f deployment.yaml
kubectl delete -f service.yaml
```

## Folder Structure

```
.
├── Dockerfile              # Dockerfile to containerize the app
├── app.js                  # Node.js app code
├── deployment.yaml         # Kubernetes Deployment configuration
├── service.yaml            # Kubernetes Service configuration
├── package.json            # Node.js dependencies
└── README.md               # Project documentation
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
