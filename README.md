# Hello-Node
This project demonstrates deploying a Node.js application on a Kubernetes cluster with horizontal pod autoscaling (HPA). The application is a simple Express server that responds with "Hello World" at the root endpoint.

## Prerequisites

Ensure you have the following installed before you begin:

- **Docker**
- **Kubernetes**
- **kubectl**
- **hey** (or other load testing tools): For stress testing the application.
  - Install `hey`: [https://github.com/rakyll/hey](https://github.com/rakyll/hey)

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/AbhiVastrad/Hello-node.git
cd Hello-node
```

### 2.Dependency Installation

```bash
npm start
```

It installs all the necessary packages and libraries listed in the package.json. This ensures that your project has everything it needs to run properly.

### 3. Build Docker Image

Ensure you have Docker running and build the Docker image:

```bash
docker build -t your-dockerhub-username/Hello-node:latest .
```

### 4. Push the Image to Docker Hub

```bash
docker push your-dockerhub-username/Hello-node:latest
```

Replace `your-dockerhub-username` with your Docker Hub username.

---

## Kubernetes Setup

### 1. Create the Kubernetes Deployment

Deploy the Node.js application on your Kubernetes cluster:

```bash
kubectl apply -f kubernetes/deployment.yaml
```

### 2. Expose the Application via Service

```bash
kubectl apply -f kubernetes/service.yaml
```

### 3. Set Up Horizontal Pod Autoscaling (HPA)

```bash
kubectl apply -f kubernetes/hpa.yaml
```

### 4. Verify Deployment

You can check the status of the deployment, service, and HPA:

```bash
kubectl get deployments
kubectl get svc
kubectl get hpa
```

---

## Load Testing

Use `hey` or another tool to simulate traffic and observe the autoscaling behavior:

```bash
hey -n 10000 -c 100 http://localhost:3000/
```

- `-n 10000`: The number of requests to send.
- `-c 100`: The number of concurrent users

## Monitoring Autoscaling

You can monitor how the pods are scaled using the following command:

```bash
kubectl get hpa -w
```

This will display real-time scaling of the pods.

## Screencast and Screenshots

### Screencast: https://drive.google.com/drive/folders/1vvRWC2-PI1EoKU3lczPPMjFjxXGyAm4z?usp=sharing


By following the steps outlined in this document, you should be able to successfully deploy, scale, and monitor a Node.js application on Kubernetes.
