# kub-pod-svc
Deploy

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

Updates to kubeconfig secret



- name: Set up kubeconfig
  run: |
    mkdir -p $HOME/.kube
    echo "${{ secrets.KUBECONFIG_SECRET }}" > $HOME/.kube/config
    export KUBECONFIG=$HOME/.kube/config
    kubectl config view
    kubectl cluster-info

    Self-hosted Runner
    on:
  push:
    branches:
      - main

jobs:
  deploy:
    # Use a self-hosted runner that is on the same network as your cluster.
    # If you instead have a publicly reachable API endpoint, you can keep ubuntu-latest.
    runs-on: [self-hosted, k8s-access]

    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Set up kubeconfig
      run: |
        # Create the .kube directory if it doesn't exist
        mkdir -p $HOME/.kube
        # Write the kubeconfig secret to a file
        echo "${{ secrets.KUBECONFIG_SECRET }}" > $HOME/.kube/config
        # Export the KUBECONFIG variable so kubectl can locate the config
        export KUBECONFIG=$HOME/.kube/config
        # View the kubeconfig for confirmation (sensitive data is redacted in logs)
        kubectl config view || echo "Failed to view kubeconfig"

    - name: Verify kubectl installation
      run: |
        # Check if kubectl is available on the runner
        which kubectl || echo "kubectl is not installed on the runner"
        kubectl version --client || echo "Ensure kubectl is correctly configured"

    - name: Debug Kubeconfig
      run: |
        echo "Testing kubeconfig connection..."
        kubectl config current-context || echo "No current context found. Verify kubeconfig."
        kubectl cluster-info || echo "Failed to connect to the cluster."
        kubectl get nodes || echo "Failed to get nodes from the Kubernetes cluster"

    - name: Apply Kubernetes manifests
      run: |
        # Change directory to the folder containing your manifests
        cd kube
        # (Optional) View the current kubeconfig and cluster connection details
        kubectl config view
        kubectl get nodes  # to verify connectivity
        # Apply your manifests
        kubectl apply -f nginxpod.yaml
        kubectl apply -f prometheuspod.yaml 
        kubectl apply -f grafanapod.yaml


on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Set up kubeconfig
      run: |
        
        echo "${{ secrets.KUBECONFIG_SECRET }}" > kubeconfig
        export KUBECONFIG=$PWD/kubeconfig
        kubectl config view || echo "Failed to view kubeconfig"
    
      
    - name: Verify kubectl installation
      run: |
        # Check if kubectl is available
        which kubectl || echo "kubectl is not installed on the runner"
        kubectl version --client || echo "Ensure kubectl is correctly configured"

    - name: Debug Kubeconfig
      run: |
          echo "Testing kubeconfig connection..."
          kubectl config current-context || echo "No current context found. Verify kubeconfig."
          kubectl cluster-info || echo "Failed to connect to the cluster."
          kubectl cluster-info || echo "Failed to connect to the Kubernetes cluster"
          kubectl get nodes || echo "Failed to get nodes from the Kubernetes cluster"

    - name: Apply Kubernetes manifests
      run: |
        # Applying manifests to the Kubernetes cluster
        cd kube
        kubectl config view
        kubectl get nodes  # To verify connection
        kubectl apply -f nginxpod.yaml
        kubectl apply -f prometheuspod.yaml 
        kubectl apply -f grafanapod.yaml 




