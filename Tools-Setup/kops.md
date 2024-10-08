Creating a fully automated production-grade Kubernetes (K8s) cluster from scratch involves several steps. This process will include setting up AWS infrastructure, installing Kubernetes, and configuring monitoring, logging, and security. Here’s a comprehensive script to automate the setup of a production-grade Kubernetes cluster using `kops` on AWS.

### Prerequisites

- **AWS Account**: Ensure you have an AWS account with necessary permissions.
- **AWS CLI**: Install and configure AWS CLI.
- **kops**: Install `kops`.
- **kubectl**: Install `kubectl`.
- **IAM Permissions**: Ensure you have the necessary IAM roles and policies for S3, Route 53, EC2, etc.

### Complete Automation Script

```bash
#!/bin/bash

# Function to handle errors
handle_error() {
    echo "Error: $1"
    exit 1
}

# Check for required commands
for cmd in curl unzip aws kops kubectl; do
    if ! command -v "$cmd" &> /dev/null; then
        handle_error "$cmd is not installed. Please install it first."
    fi
done

# Set environment variables
export AWS_REGION=us-east-1
export KOPS_CLUSTER_NAME=my-cluster.example.com
export KOPS_STATE_STORE=s3://your-kops-state-store
export DNS_ZONE_ID=your-hosted-zone-id

# Update package list and install dependencies
sudo apt update || handle_error "Failed to update package list."

# Download and install kubectl
curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.25.0/bin/linux/amd64/kubectl || handle_error "Failed to download kubectl."
chmod +x ./kubectl || handle_error "Failed to set execute permissions on kubectl."
sudo mv ./kubectl /usr/local/bin/kubectl || handle_error "Failed to move kubectl to /usr/local/bin."

# Download and install kOps
curl -LO https://github.com/kubernetes/kops/releases/download/v1.25.0/kops-linux-amd64 || handle_error "Failed to download kOps."
chmod +x kops-linux-amd64 || handle_error "Failed to set execute permissions on kOps."
sudo mv kops-linux-amd64 /usr/local/bin/kops || handle_error "Failed to move kOps to /usr/local/bin."

# Configure AWS CLI
aws configure set aws_access_key_id YOUR_AWS_ACCESS_KEY_ID || handle_error "Failed to set AWS Access Key."
aws configure set aws_secret_access_key YOUR_AWS_SECRET_ACCESS_KEY || handle_error "Failed to set AWS Secret Key."
aws configure set region $AWS_REGION || handle_error "Failed to set AWS region."

# Generate SSH key if not already exists
if [ ! -f "$HOME/.ssh/id_rsa" ]; then
    ssh-keygen -N "" -f "$HOME/.ssh/id_rsa" || handle_error "Failed to generate SSH key."
else
    echo "SSH key already exists."
fi

# Create an S3 bucket for kOps state storage if not already created
aws s3api head-bucket --bucket $(echo $KOPS_STATE_STORE | cut -d'/' -f3) 2>/dev/null || \
    aws s3 mb $KOPS_STATE_STORE || handle_error "Failed to create S3 bucket."

# Create Route 53 hosted zone if not already created
aws route53 list-hosted-zones | grep $DNS_ZONE_ID || \
    handle_error "DNS hosted zone with ID $DNS_ZONE_ID not found. Please create it manually."

# Create Kubernetes cluster using kOps
kops create cluster \
    --node-count=3 \
    --master-size=t3.medium \
    --node-size=t3.medium \
    --master-volume-size=100 \
    --node-volume-size=100 \
    --zones=us-east-1a,us-east-1b,us-east-1c \
    --name=${KOPS_CLUSTER_NAME} \
    --dns-zone=${DNS_ZONE_ID} || handle_error "Failed to create cluster."

# Edit and review cluster configuration if needed
kops edit cluster ${KOPS_CLUSTER_NAME} || handle_error "Failed to edit cluster configuration."

# Apply the cluster configuration
kops update cluster ${KOPS_CLUSTER_NAME} --yes || handle_error "Failed to update cluster."

# Validate the cluster
kops validate cluster || handle_error "Cluster validation failed."

# Install Calico network plugin
kubectl apply -f https://docs.projectcalico.org/manifests/calico.yaml || handle_error "Failed to install Calico network plugin."

# Install Helm for application management
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 || handle_error "Failed to download Helm install script."
chmod 700 get_helm.sh || handle_error "Failed to set execute permissions on Helm install script."
./get_helm.sh || handle_error "Failed to install Helm."

# Install monitoring stack (Prometheus & Grafana)
kubectl create namespace monitoring || handle_error "Failed to create monitoring namespace."
kubectl apply -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/main/bundle.yaml || handle_error "Failed to install Prometheus Operator."
kubectl apply -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/main/example/prometheus-example.yaml || handle_error "Failed to install Prometheus."
kubectl apply -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/main/example/grafana-example.yaml || handle_error "Failed to install Grafana."

# Install Fluentd for logging
kubectl apply -f https://raw.githubusercontent.com/fluent/fluentd-kubernetes-daemonset/master/docker-image/v1.12/debian/fluentd-kubernetes-daemonset.rb || handle_error "Failed to install Fluentd for logging."

# Update .bashrc to include KOPS_STATE_STORE environment variable
if ! grep -q "KOPS_STATE_STORE" "$HOME/.bashrc"; then
    echo "export KOPS_STATE_STORE=$KOPS_STATE_STORE" >> "$HOME/.bashrc" || handle_error "Failed to update .bashrc."
fi

echo "Setup script completed successfully. Please reload your shell or run 'source ~/.bashrc'."
```

### Instructions for Use:

1. **Save the Script**:
   Save the above script to a file, for example `setup-production-k8s.sh`.

2. **Modify Placeholders**:
   Replace the following placeholders:
   - `YOUR_AWS_ACCESS_KEY_ID` and `YOUR_AWS_SECRET_ACCESS_KEY` with your AWS credentials.
   - `s3://your-kops-state-store` with your S3 bucket URL.
   - `my-cluster.example.com` with your desired cluster name.
   - `your-hosted-zone-id` with your Route 53 hosted zone ID.

3. **Make the Script Executable**:
   ```bash
   chmod +x setup-production-k8s.sh
   ```

4. **Run the Script**:
   ```bash
   ./setup-production-k8s.sh
   ```

### Summary:

- **Initial Setup**: Installs necessary tools and sets up AWS configurations.
- **Cluster Creation**: Creates and configures the Kubernetes cluster using `kops`.
- **Network Plugin**: Installs Calico for networking.
- **Application Management**: Installs Helm for managing Kubernetes applications.
- **Monitoring and Logging**: Sets up Prometheus, Grafana, and Fluentd for monitoring and logging.
- **Environment Variables**: Updates `.bashrc` to include `KOPS_STATE_STORE`.

This script provides a comprehensive automation for setting up a production-grade Kubernetes cluster. Depending on your specific requirements, you may need to further customize the script, especially for advanced security configurations, custom monitoring solutions, or additional applications.



# LAB 


It looks like you’ve provided a comprehensive set of instructions for deploying a Kubernetes application using kOps on AWS. The process involves setting up a Kubernetes cluster with kOps, deploying a pod, exposing it through a LoadBalancer service, and then cleaning up resources. Here's a more structured version of your guide with some enhancements for clarity and completeness:

---

# Deploying an Application into Kubernetes Using kOps

kOps simplifies the creation, destruction, and maintenance of Kubernetes clusters, particularly for AWS and GCE. This guide will walk you through setting up a Kubernetes cluster on AWS, deploying an application, and cleaning up the resources.

## Prerequisites

- AWS account with appropriate permissions.
- Basic knowledge of AWS EC2, S3, and Kubernetes.
- AWS CLI installed on your local machine.

## Lab Steps

### Lab 1: Launch Kubernetes Cluster in AWS (EC2)

#### Task 1: Launch Anchor EC2 Instance

1. **Launch an EC2 Instance**: 
   - Launch an Ubuntu 22.04 EC2 instance.
   - Ensure that port 22 (SSH) is open in the security group.

2. **Connect to Your EC2 Instance**: SSH into the EC2 instance.

3. **Update Hostname**:
   ```bash
   sudo hostnamectl set-hostname kubernetes
   ```

4. **Install Utilities**:
   ```bash
   sudo apt update
   sudo apt install nano curl wget awscli -y
   ```

5. **Create Setup Script**: 
   ```bash
   vi install-kops-tool.sh
   ```
   Paste the following script:
   ```bash
   #!/bin/bash

   echo "Enter AWS Access Key:"
   read awsaccess

   echo "Enter AWS Secret Key:"
   read awssecret

   echo "Enter Cluster Name (ex: my-kube.k8s.local):"
   read clname

   echo "Enter an AZ for the cluster (ex: us-east-1a):"
   read az

   sudo apt update

   # Download kubectl and kOps
   curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.25.0/bin/linux/amd64/kubectl
   chmod +x ./kubectl
   sudo mv ./kubectl /usr/local/bin/kubectl

   sudo curl -LO https://github.com/kubernetes/kops/releases/download/v1.25.0/kops-linux-amd64
   sudo chmod +x kops-linux-amd64
   sudo mv kops-linux-amd64 /usr/local/bin/kops

   # Configure AWS CLI
   aws configure set aws_access_key_id $awsaccess
   aws configure set aws_secret_access_key $awssecret

   # Generate SSH key for cluster login
   ssh-keygen -N "" -f $HOME/.ssh/id_rsa

   # Create S3 bucket for kOps state storage
   aws s3 mb s3://$clname

   # Set S3 bucket as environment variable
   export KOPS_STATE_STORE=s3://$clname

   # Create and update Kubernetes cluster
   kops create cluster --node-count=2 --master-size="t3.medium" --node-size="t3.medium" --master-volume-size=30 --node-volume-size=30 --zones=$az --name $clname
   kops get cluster
   kops update cluster $clname --yes

   # Update .bashrc
   echo "export KOPS_STATE_STORE=s3://$clname" >> ~/.bashrc
   ```

6. **Run the Script**:
   ```bash
   chmod +x install-kops-tool.sh
   ./install-kops-tool.sh
   ```

   - Enter your AWS Access Key, Secret Key, Cluster Name, and Availability Zone when prompted.

7. **Verify Cluster Creation**:
   ```bash
   kops get cluster
   kops export kubecfg --admin
   kops validate cluster
   ```

   - Validation may take 10+ minutes. You can use `--wait 10m --count 3` to wait and check status.

8. **Check EC2 Instances**:
   - Confirm that the master and worker nodes are up in the AWS EC2 dashboard.

9. **Stopping Instances**:
   - To stop the EC2 instances, adjust the Auto Scaling Group settings to zero.

#### Task 2: Create a Pod Using YAML

1. **Create Pod YAML File**:
   ```bash
   vi 2048-pod.yaml
   ```
   Add the following content:
   ```yaml
   apiVersion: v1
   kind: Pod
   metadata:
     name: 2048-pod
     labels:
       app: 2048-ws
   spec:
     containers:
     - name: 2048-container
       image: blackicebird/2048
       ports:
         - containerPort: 80
   ```

2. **Apply the Pod Configuration**:
   ```bash
   kubectl apply -f 2048-pod.yaml
   kubectl get pods
   ```

#### Task 3: Setup Load Balancer Service

1. **Create Service YAML File**:
   ```bash
   vi game-svc.yaml
   ```
   Add the following content:
   ```yaml
   apiVersion: v1
   kind: Service
   metadata:
     name: game-svc
   spec:
     selector:
       app: 2048-ws
     ports:
     - protocol: TCP
       port: 80
       targetPort: 80
     type: LoadBalancer
   ```

2. **Apply the Service Configuration**:
   ```bash
   kubectl apply -f game-svc.yaml
   kubectl describe svc game-svc
   ```

   - The LoadBalancer service might take a few minutes to get an external IP.

3. **Access the Application**:
   - Go to the AWS EC2 dashboard, find the Load Balancer, and copy its DNS name.
   - Paste the DNS name into your browser to access the 2048 game.

#### Task 4: Cleanup

1. **Delete Resources**:
   ```bash
   kubectl delete -f game-svc.yaml
   kubectl delete -f 2048-pod.yaml
   ```

2. **Delete the Kubernetes Cluster**:
   ```bash
   kops delete cluster --name=kube102.k8s.local --yes
   ```

3. **Delete the S3 Bucket**:
   - You can delete the S3 bucket manually through the AWS S3 console or use the AWS CLI:
     ```bash
     aws s3 rb s3://kube102.k8s.local --force
     ```

---

This guide covers the essentials for deploying an application into Kubernetes using kOps, including setting up the cluster, deploying a pod, exposing it with a LoadBalancer, and cleaning up resources. Adjust the details based on your specific requirements and environment.
