# kub-pod-svc


In this Project, I created and deployed Grafana, Prometheus, and Nginx pods with their associated NodePort services using Docker Desktop with Kubernetes enabled using the following steps. However, there are several prerequites that are important before the project can be completed:


# Pre-requisite:

  1. **Set Up Docker Desktop with Kubernetes**

     - Install Docker Desktop [with Kubernetes Enabled]
     - Verify Kubernetes is running by executing `kubectl get nodes`.

  2. Install and verify kubectl command line on your local machine


1. **Create YAML Files for Deployments**

   - For each application (Grafana, Prometheus, and Nginx), create separate Kubernetes YAML files to   
     define the Deployment and their associated Service resources (Kube directory)

2. **Apply the YAML Files**

   - Use `kubectl apply -f <filename>.yaml` for each YAML file to deploy the pods and services.

3. **Verify Deployments and Services**

   - Check the status of the pods: `kubectl get pods`.

   - Verify the services: `kubectl get svc`.

4. **Access the Applications**

   - Use the NodePort values defined in the YAML files to access the applications in your browser. 

- **Grafana**: Exposed on NodePort `32000`, accessible at `<NodeIP>:32000`

- **NGINX**: Exposed on NodePort `30001`, accessible at `<NodeIP>:30001`

- **Prometheus**: Exposed on NodePort `32001`, accessible at `<NodeIP>:32001`

- **Screenshots**: Testing of the pods and services created. 

For example: 

     - Grafana: `http://localhost:32000`

     - Prometheus: `http://localhost:30001`
     
     - Nginx: `http://localhost:32001`    


# Overall, this setup ensures that each application is deployed as a pod and exposed via a complementary NodePort service, enabling their accessibility from your local machine.












