# MySQL Database Deployment Guide

This guide explains how to set up a MySQL database container in Kubernetes.

## Prerequisites

- Minikube installed
- kubectl CLI tool
- Docker running

## Installation Steps

1. Start Minikube for local development:
```bash
minikube start
```

2. Apply Kubernetes configurations in the following order:
```bash
# Create storage class
kubectl apply -f /k8s/mysql/

 
```

## Accessing the Database Locally

1. View the service details:
```bash
kubectl get svc
```

2. Set up port forwarding to access MySQL from your local machine:
This is only for the local development, on the production use the name "mysql" as the host
```bash
kubectl port-forward svc/<service-name> <local-port>:3306
```

Example:
```bash
kubectl port-forward svc/mysql-service 30006:3306
```

## Database Connection Details

- Host: `localhost` (when using port-forward)
- Port: 3306
- Username: admin
- Password: admin
- Database: demo

## Troubleshooting

To check the status of your pods:
```bash
kubectl get pods
```

To view pod logs:
```bash
kubectl logs <pod-name>
```

## Cleaning Up

To delete all resources:
```bash
kubectl delete -f /k8s/mysql/
 
```

