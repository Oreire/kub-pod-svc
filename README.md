# kub-pod-svc


In this Project, Grafana, Prometheus and Nginx pods are deployed with their associated NodPorts services that afford access. However, there are several prerequites that are important before the project can be completed:


# Pre-requisite:

  1. Install Docker Desktop [with Kubernetes Enabled]
  
  2. Install kubectl command line on your local machine


# Implementation:

   1. GitHub Actions Pipelibne workflow created for automated provisioning

   2. Directory created to store the Kubernetes artifacts namely the K8S deployment YAML manifests

   3. A documentation of the Project is provided with README


Key Project Outcomes:

- **Grafana**: Exposed on NodePort `32000`, accessible at `<NodeIP>:32000`

- **NGINX**: Exposed on NodePort `30001`, accessible at `<NodeIP>:30001`

- **Prometheus**: Exposed on NodePort `32001`, accessible at `<NodeIP>:32001`

- **Screenshots**: Tesing of the pods and services created. 













