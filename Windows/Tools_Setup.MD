# Tools installation on Ubuntu (Windows)

**Pre-Requisites:** 

- wsl2
- ubuntu 

## Install Docker in ubuntu

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


## Installing K8s using Minikube on Ubuntu 

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
