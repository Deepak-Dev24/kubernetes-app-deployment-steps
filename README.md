# Command Reference for React App Deployment on Kubernetes with Docker and Minikube

This document serves as a reference guide for deploying a React application using Docker, Kubernetes, and Minikube. Below are the steps and corresponding commands for the complete deployment process.

## Cloning the Repository
```sh
git clone https://github.com/Deepak-Dev24/react.git
```
Clones the React repository from GitHub to your local machine.

```sh
cd react
```
Navigates to the React project directory.

## Installing Dependencies and Starting React App
```sh
npm install
```
Installs the required dependencies for the React project.

```sh
npm start
```
Starts the React development server.

## Building and Pushing Docker Image
```sh
docker login
```
Logs into Docker Hub using your credentials.

```sh
docker info
```
Displays detailed information about your Docker installation and configuration.

```sh
docker build -t deepak2633/new-react-app:v1 .
```
Builds a Docker image for the React app and tags it as `deepak2633/new-react-app:v1`.

```sh
docker images
```
Lists all available Docker images on your system.

```sh
docker push deepak2633/new-react-app:v1
```
Pushes the `new-react-app:v1` Docker image to Docker Hub.

## Setting Up Minikube
```sh
minikube status
```
Checks the status of the Minikube cluster.

```sh
minikube start
```
Starts the Minikube virtual machine.

## Deploying the Application to Kubernetes
```sh
kubectl create deployment mywebapp --image=deepak2633/webapp-demo:01
```
Creates a deployment named `mywebapp` using the `webapp-demo:01` Docker image.

```sh
kubectl get deployment
```
Lists all deployments in the Kubernetes cluster.

```sh
kubectl get pods
```
Lists all pods running in the cluster.

```sh
kubectl describe pod <pod-name>
```
Provides detailed information about a specific pod to help with debugging.

## Using Minikube Dashboard
```sh
minikube dashboard
```
Launches the Minikube Dashboard for visual management of your Kubernetes resources.

```sh
minikube dashboard --url
```
Provides the URL to access the Minikube dashboard in a browser.

## Checking Logs
```sh
kubectl logs <pod-name>
```
Retrieves logs from the specified pod.

## Exposing the Deployment
```sh
kubectl expose deployment mywebapp --type=NodePort --port=3000
```
Exposes the `mywebapp` deployment to be accessible externally on port `3000` via NodePort.

```sh
kubectl expose pod <pod-name> --type=NodePort --port=80 --target-port=8080 --name=my-pod-service
```
Exposes a specific pod to be accessible externally through a NodePort with specified port mappings.

## Deleting a Service
```sh
kubectl delete svc my-pod-service
```
Deletes a service named `my-pod-service` from the Kubernetes cluster.

## Updating Deployment Image
```sh
kubectl set image deployment mywebapp webapp-demo=deepak2633/webapp-demo:06
```
Updates the `mywebapp` deployment to use the `webapp-demo:06` Docker image.

## Deploying the React App in Kubernetes
```sh
kubectl create deployment my-react-app --image=deepak2633/new-react-app:v1
```
Creates a deployment for your React app using the `new-react-app:v1` Docker image.

```sh
kubectl expose deployment my-react-app --type=NodePort --port=80 --target-port=3000
```
Exposes the React app (`my-react-app`) on port `80` externally, with the internal target port `3000`.

## Listing Services
```sh
kubectl get services
```
Lists all services in the cluster, including NodePort services.

---
This document includes all necessary commands for deploying your React application using Docker, Kubernetes, and Minikube. Let me know if you need any modifications or further clarifications!

