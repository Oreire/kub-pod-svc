# kub-pod-svc


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













