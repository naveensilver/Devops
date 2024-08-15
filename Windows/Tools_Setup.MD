# Tools installation on Ubuntu (Windows)

**Pre-Requisites:** 

- wsl2
- ubuntu 

## Install Docker in ubuntu WSL2

Installing Docker on Ubuntu within Windows Subsystem for Linux (WSL) involves a few steps to ensure that Docker works correctly in this environment. Here's a step-by-step guide:

### 1. **Set Up WSL 2**

Ensure that you are using WSL 2, as it provides better compatibility for Docker. You can check the version of WSL you're using and update it if needed:

1. **Check WSL version:**

   Open PowerShell and run:

   ```powershell
   wsl --list --verbose
   ```

   If it shows version 1, you need to upgrade to version 2.

2. **Upgrade to WSL 2 (if needed):**

   Follow [Microsoft's guide](https://docs.microsoft.com/en-us/windows/wsl/install) to upgrade to WSL 2 if you're not already using it.

### 2. **Install Docker in Ubuntu WSL**

1. **Update Package Information:**

   Open your WSL terminal (Ubuntu) and update the package list:

   ```bash
   sudo apt update
   ```

2. **Install Required Packages:**

   Install the necessary packages for Docker:

   ```bash
   sudo apt install apt-transport-https ca-certificates curl software-properties-common
   ```

3. **Add Docker’s Official GPG Key:**

   Import Docker’s official GPG key:

   ```bash
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
   ```

4. **Add Docker Repository:**

   Add Docker’s APT repository:

   ```bash
   sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
   ```

5. **Update Package Index Again:**

   Update the package list to include Docker’s packages:

   ```bash
   sudo apt update
   ```

6. **Install Docker:**

   Install Docker CE (Community Edition):

   ```bash
   sudo apt install docker-ce
   ```

7. **Start and Enable Docker:**

   Start Docker and enable it to run on boot:

   ```bash
   sudo service docker start
   sudo systemctl enable docker
   ```

8. **Add Your User to the Docker Group:**

   To run Docker commands without `sudo`, add your user to the `docker` group:

   ```bash
   sudo usermod -aG docker $USER
   ```

   You will need to log out and back in for this change to take effect. Alternatively, you can use:

   ```bash
   newgrp docker
   ```

### 3. **Verify Docker Installation**

1. **Check Docker Version:**

   Verify that Docker is installed and running:

   ```bash
   docker --version
   ```

2. **Run a Test Container:**

   Run a test container to ensure Docker is working:

   ```bash
   docker run hello-world
   ```

### 4. **Access Docker from Windows (Optional)**

To use Docker from Windows (outside WSL), you may need Docker Desktop for Windows, which provides integration with WSL 2.

1. **Download and Install Docker Desktop:**

   Download Docker Desktop from [Docker’s website](https://www.docker.com/products/docker-desktop) and install it.

2. **Configure Docker Desktop to Use WSL 2:**

   Open Docker Desktop, go to **Settings** > **General**, and ensure that the option to **Use the WSL 2 based engine** is enabled.

3. **Enable Integration with WSL Distributions:**

   In Docker Desktop settings, go to **Resources** > **WSL Integration** and enable integration with your Ubuntu distribution.

By following these steps, you should have Docker installed and working on your Ubuntu WSL setup. If you encounter issues, make sure to check Docker’s [official documentation](https://docs.docker.com/docker-for-windows/wsl/) for troubleshooting tips related to WSL and Docker integration.


## Installing K8s using Minikube on Ubuntu WSL2

Installing Kubernetes on Ubuntu within WSL 2 involves setting up a Kubernetes cluster. While WSL 2 provides a great environment for testing and development, setting up a production-ready Kubernetes cluster is more complex and typically involves using a tool like Minikube or kind (Kubernetes IN Docker) for local development.

Here’s a step-by-step guide to installing Kubernetes using Minikube, which is well-suited for development purposes:

### **1. Install Minikube**

Minikube is a tool that makes it easy to run Kubernetes locally. 

1. **Download Minikube:**

   Download the Minikube binary from the official Minikube GitHub repository. Check the latest release version on [Minikube releases](https://github.com/kubernetes/minikube/releases) and replace `vX.X.X` with the version number:

   ```bash
   curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
   ```

2. **Install Minikube:**

   Move the binary to a directory in your `PATH` and make it executable:

   ```bash
   sudo install minikube-linux-amd64 /usr/local/bin/minikube
   ```

3. **Verify Minikube Installation:**

   Check that Minikube is installed correctly:

   ```bash
   minikube version
   ```

### **2. Install kubectl**

`kubectl` is the command-line tool used to interact with Kubernetes clusters.

1. **Download kubectl:**

   Download the latest version of `kubectl`:

   ```bash
   curl -LO "https://dl.k8s.io/release/v1.27.3/bin/linux/amd64/kubectl"
   ```

   Replace `v1.27.3` with the latest stable version if needed.

2. **Install kubectl:**

   Move the binary to a directory in your `PATH` and make it executable:

   ```bash
   chmod +x ./kubectl
   sudo mv ./kubectl /usr/local/bin/kubectl
   ```

3. **Verify kubectl Installation:**

   Check that `kubectl` is installed correctly:

   ```bash
   kubectl version --client
   ```

### **3. Start Minikube**

1. **Start Minikube:**

   Initialize a Minikube cluster. You might need to specify a driver if it doesn't automatically choose one (like `docker` for WSL):

   ```bash
   minikube start --driver=docker
   ```

   This command starts a Minikube cluster using Docker as the driver. Make sure Docker is running, as Minikube uses Docker containers to create the Kubernetes cluster.

2. **Verify Minikube Status:**

   Check the status of your Minikube cluster:

   ```bash
   minikube status
   ```

### **4. Access Kubernetes Dashboard (Optional)**

Minikube can deploy a Kubernetes Dashboard, which provides a web-based interface for managing your Kubernetes cluster.

1. **Enable the Dashboard:**

   ```bash
   minikube dashboard
   ```

   This command will open the Kubernetes Dashboard in your default web browser.

### **5. Use kubectl with Minikube**

You can now use `kubectl` to interact with your Minikube Kubernetes cluster. For example:

1. **Get Cluster Nodes:**

   ```bash
   kubectl get nodes
   ```

2. **Deploy Applications:**

   You can create Kubernetes deployments, services, and other resources using `kubectl` commands. 

### **Troubleshooting**

- **WSL 2 Networking Issues:**
  Ensure that WSL 2 has proper network access. Sometimes networking issues can prevent Minikube from starting properly.

- **Check Minikube Logs:**
  If Minikube doesn’t start or behaves unexpectedly, check the logs:

  ```bash
  minikube logs
  ```

- **Ensure Docker Is Running:**
  Minikube requires Docker to be running, as it uses Docker containers to create the Kubernetes cluster.

By following these steps, you should have a functional Kubernetes cluster running locally on Ubuntu within WSL 2. This setup is great for development and testing purposes.


## Install Terraform Ubuntu WSL2

Installing Terraform on WSL 2 with Ubuntu involves a few straightforward steps. Here’s a detailed guide to get you up and running:

### **1. Update Your Package List**

Start by updating your package list to ensure you have the latest information about available packages:

```bash
sudo apt update
```

### **2. Install Required Dependencies**

Install necessary dependencies if they aren't already installed:

```bash
sudo apt install -y gnupg software-properties-common curl
```

### **3. Add the HashiCorp APT Repository**

HashiCorp provides an official APT repository for installing Terraform. Follow these steps to add the repository:

1. **Add HashiCorp’s GPG Key:**

   ```bash
   curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
   ```

2. **Add the HashiCorp APT Repository:**

   Add the HashiCorp repository to your system's sources list:

   ```bash
   sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
   ```

   Here, `$(lsb_release -cs)` dynamically inserts your Ubuntu release codename (like `focal` for 20.04 or `jammy` for 22.04).

### **4. Install Terraform**

Update your package list again to include the new HashiCorp repository and install Terraform:

```bash
sudo apt update
sudo apt install terraform
```

### **5. Verify the Installation**

Check that Terraform is installed correctly and verify its version:

```bash
terraform --version
```

### **Alternative Installation Method: Manual Installation**

If you prefer, you can manually download and install Terraform:

1. **Download Terraform:**

   Visit the [Terraform releases page](https://www.terraform.io/downloads.html) to find the latest version and download it. For example:

   ```bash
   curl -LO "https://releases.hashicorp.com/terraform/1.6.5/terraform_1.6.5_linux_amd64.zip"
   ```

   Replace `1.6.5` with the latest version number.

2. **Install `unzip` Utility:**

   If `unzip` is not already installed, install it:

   ```bash
   sudo apt install unzip
   ```

3. **Unzip the Downloaded File:**

   Unzip the Terraform binary:

   ```bash
   unzip terraform_1.6.5_linux_amd64.zip
   ```

4. **Move the Binary to `/usr/local/bin`:**

   Move the `terraform` binary to a directory included in your system's `PATH`:

   ```bash
   sudo mv terraform /usr/local/bin/
   ```

5. **Verify the Installation:**

   Ensure Terraform is installed correctly:

   ```bash
   terraform --version
   ```

### **6. Set Up Terraform**

1. **Create a Directory for Your Terraform Project:**

   ```bash
   mkdir my-terraform-project
   cd my-terraform-project
   ```

2. **Create a Basic Terraform Configuration File:**

   Create a file named `main.tf` with a basic configuration. For example, a simple AWS provider configuration:

   ```hcl
   provider "aws" {
     region = "us-east-1"
   }

   resource "aws_instance" "example" {
     ami           = "ami-0c55b159cbfafe1f0"
     instance_type = "t2.micro"
   }
   ```

3. **Initialize Terraform:**

   Initialize your Terraform configuration directory:

   ```bash
   terraform init
   ```

4. **Plan and Apply Your Configuration:**

   To see what changes Terraform will make:

   ```bash
   terraform plan
   ```

   To apply the configuration and create resources:

   ```bash
   terraform apply
   ```

By following these steps, you should have Terraform installed and configured on your WSL 2 Ubuntu environment, ready for managing your infrastructure as code.


## Install Ansible WSL2 

To install Ansible on Ubuntu running within WSL 2 (Windows Subsystem for Linux 2), follow these steps:

### **1. Update Your Package List**

Start by updating your package list to ensure you have the latest information about available packages:

```bash
sudo apt update
```

### **2. Install Required Dependencies**

Install any necessary dependencies for Ansible:

```bash
sudo apt install -y software-properties-common
```

### **3. Add the Ansible PPA (Personal Package Archive)**

Ansible is available in the official Ubuntu repositories, but it is often not the latest version. To ensure you get the latest version, you can add the Ansible PPA:

1. **Add the Ansible PPA:**

   ```bash
   sudo add-apt-repository ppa:ansible/ansible
   ```

2. **Update Package List Again:**

   ```bash
   sudo apt update
   ```

### **4. Install Ansible**

Now, install Ansible:

```bash
sudo apt install -y ansible
```

### **5. Verify the Installation**

Check that Ansible is installed correctly and verify its version:

```bash
ansible --version
```

### **6. Basic Configuration (Optional)**

To get started with Ansible, you might want to configure a basic inventory and playbook. Here’s a quick example:

1. **Create a Directory for Your Ansible Project:**

   ```bash
   mkdir ~/ansible-project
   cd ~/ansible-project
   ```

2. **Create an Inventory File:**

   Create a file named `inventory.ini` with the following content:

   ```ini
   [local]
   localhost ansible_connection=local
   ```

3. **Create a Simple Playbook:**

   Create a file named `playbook.yml` with a simple playbook to test:

   ```yaml
   ---
   - name: Test Playbook
     hosts: localhost
     tasks:
       - name: Print Hello World
         debug:
           msg: "Hello, World!"
   ```

4. **Run the Playbook:**

   Execute the playbook to test your Ansible setup:

   ```bash
   ansible-playbook -i inventory.ini playbook.yml
   ```

This will print `Hello, World!` if everything is set up correctly.

### **Troubleshooting**

If you encounter issues, consider the following:

- **Network Connectivity:** Ensure WSL 2 has network access and can reach necessary repositories.
- **Permissions:** You may need `sudo` for some commands.
- **WSL 2 Integration:** Ensure your WSL 2 setup is properly configured and up to date.

By following these steps, you should have Ansible installed and ready to use on your WSL 2 Ubuntu setup. You can now start automating and managing your infrastructure using Ansible!

## Install AWS CLI on Ubuntu WSL2

To install the AWS CLI (Command Line Interface) on Ubuntu running within WSL 2 (Windows Subsystem for Linux 2), follow these steps. The AWS CLI allows you to interact with AWS services from the command line.

### **1. Update Your Package List**

Start by updating your package list to ensure you have the latest information about available packages:

```bash
sudo apt update
```

### **2. Install Required Dependencies**

Install the necessary dependencies for the AWS CLI:

```bash
sudo apt install -y unzip curl
```

### **3. Download and Install the AWS CLI**

AWS CLI version 2 is the latest major version and is recommended. Here’s how to install it:

1. **Download the AWS CLI Version 2 Installer:**

   Fetch the latest AWS CLI version 2 zip file from AWS:

   ```bash
   curl "https://d1uj6qtbmh3dt5.cloudfront.net/awscli-exe-linux-x86_64.zip" -o "awscli-exe-linux-x86_64.zip"
   ```

   This URL points to the AWS CLI version 2 binary; you can check the [AWS CLI documentation](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) for the latest download link if necessary.

2. **Unzip the Installer:**

   Unzip the downloaded file:

   ```bash
   unzip awscli-exe-linux-x86_64.zip
   ```

3. **Run the Installer:**

   Install the AWS CLI:

   ```bash
   sudo ./aws/install
   ```

   This installs AWS CLI version 2 in `/usr/local/bin/aws`.

### **4. Verify the Installation**

Check that the AWS CLI is installed correctly and verify its version:

```bash
aws --version
```

### **5. Configure the AWS CLI**

You need to configure the AWS CLI with your AWS credentials and default region.

1. **Run the Configuration Command:**

   ```bash
   aws configure
   ```

   You will be prompted to enter:

   - **AWS Access Key ID:** Your AWS access key ID.
   - **AWS Secret Access Key:** Your AWS secret access key.
   - **Default region name:** The region you want to use, such as `us-east-1`.
   - **Default output format:** The format for command output, such as `json` (you can also use `text` or `table`).

   Example configuration:

   ```plaintext
   AWS Access Key ID [None]: YOUR_ACCESS_KEY_ID
   AWS Secret Access Key [None]: YOUR_SECRET_ACCESS_KEY
   Default region name [None]: us-east-1
   Default output format [None]: json
   ```

### **6. Test the AWS CLI**

Verify that the AWS CLI is configured correctly by running a simple command, such as listing your S3 buckets:

```bash
aws s3 ls
```

This command should list your S3 buckets if your credentials and region are configured correctly.

### **Troubleshooting**

If you encounter issues:

- **Network Issues:** Ensure WSL 2 has internet access.
- **Permissions:** You might need to use `sudo` for certain commands or file operations.
- **Environment Variables:** Ensure no conflicting environment variables are set that might affect AWS CLI behavior.

By following these steps, you should have the AWS CLI installed and configured on your WSL 2 Ubuntu environment. You can now use it to manage AWS resources from the command line.
