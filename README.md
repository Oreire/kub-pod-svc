# kub-pod-svc

# Automated Deployment of Kubernetes Infrastructure and Services Using Self Hosted Runner

In this Project, I created and deployed Grafana, Prometheus, and Nginx pods with their associated NodePort services using Docker Desktop with Kubernetes enabled using the following steps. However, there are several prerequites that are important before the project can be completed:


1.   # Pre-requisite:

     **Set Up Docker Desktop with Kubernetes**

     - Install Docker Desktop [with Kubernetes Enabled]
     - Verify Kubernetes is running by executing `kubectl get nodes`.

    # Install kubectl command line on your local machine

     - Verify kubectl installed using 'kubectl version' command  

2. **Create YAML Files for Deployments**

   - For each application (Grafana, Prometheus, and Nginx), create separate Kubernetes YAML files to   
     define the Deployment and their associated Service resources (Kube directory)

3. **Apply the YAML Files**

   - Use `kubectl apply -f <filename>.yaml` for each YAML file to deploy the pods and services.

4. **Verify Deployments and Services**

   - Check the status of the pods: `kubectl get pods`.

   - Verify the services: `kubectl get svc`.

5. **Access the Applications**

   - Use the NodePort values defined in the YAML files to access the applications in your browser. 

- **Grafana**: Exposed on NodePort `31444`, accessible at `<NodeIP>:31444`

- **NGINX**: Exposed on NodePort `31502`, accessible at `<NodeIP>:31502`

- **Prometheus**: Exposed on NodePort `31693`, accessible at `<NodeIP>:31693`

- **Screenshots**: Testing of the pods and services created. 

For example: 

     - Grafana: `http://localhost:31444`

     - Prometheus: `http://localhost:31502`
     
     - Nginx: `http://localhost:31693`    


#  Overall, this setup ensures that each application is deployed as a pod and exposed via a complementary NodePort service, enabling their accessibility from your local machine.

# The Challenegs of Deploying  Kubernetes services and pods with Docker Desktop Using GitHub Actions.

### 1. **Docker Desktop's Kubernetes Limitations**:
   - Docker Desktop includes a lightweight Kubernetes cluster primarily for local development and testing, which is not designed for production-grade deployments. Hence, limited scalability, lack of high availability, and restricted resource allocation are common inherent issues.

### 2. **Networking Challenges**:
   - Docker Desktop's Kubernetes cluster runs within a virtualized environment, which can create networking complexities. Therefore, accessing services and pods externally may require additional configuration, such as port forwarding or exposing services via `NodePort`.

### 3. **Authentication and Configuration**:
   - GitHub Actions workflows often require access to the Kubernetes cluster via `kubeconfig`. Managing and securely storing the `kubeconfig` file or credentials can be challenging, especially when integrating with Docker Desktop's Kubernetes. The problem led to the use of self hosted runner to implemnet this project. The challenge is being taken up in an ongoing and more comprehensive K8S Project.

### 4. **Resource Constraints**:
   - Docker Desktop's Kubernetes cluster shares resources with the host machine. If the host has limited CPU or memory, it can impact the performance and stability of the cluster, especially during CI/CD pipeline execution.

### 5. **Lack of Persistent Storage**:
   - Docker Desktop's Kubernetes cluster may not support advanced storage solutions required for stateful applications. This can limit the types of workloads you can deploy.

### 6. **Compatibility Issues**:
   - Docker Desktop's Kubernetes version may not always align with the versions used in production environments. This can lead to discrepancies and unexpected behavior when transitioning deployments from local to production clusters.

### 7. **Workflow Complexity**:
   - Configuring GitHub Actions to interact with Docker Desktop's Kubernetes cluster can be complex. You need to ensure that the runner has access to the cluster, the necessary tools (like `kubectl`) are installed, and the environment is properly set up.

### Recommendations:
- It ia advocated that Docker Desktop's Kubernetes cluster be restricted for local testing and development only.
- However, ensure proper configuration of networking, authentication, and resource allocation when using Docker Desktop.
- For production deployments, using a managed Kubernetes service like Amazon Elastic Kubernetes Service (EKS), Azure Kubernetes Service (AKS) and Google Kubernetes Engine (GKE) are optimal.

