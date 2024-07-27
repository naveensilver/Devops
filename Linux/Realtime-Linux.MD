# Real-Time Linux Commands for DevOps Engineers

## Linux Commands Documentation for DevOps Engineers

**Author: Naveen Thurkapally**

### 1. System Monitoring and Performance

- **`top`**
  - **Use Case:** Monitor real-time system performance, CPU usage, memory usage, and running processes.
  - **Command:** `top`
  - **Example:** View the top processes consuming the most resources.

- **`htop`**
  - **Use Case:** Enhanced version of `top` with a more user-friendly interface and additional features.
  - **Command:** `htop`
  - **Example:** Navigate through processes and kill them directly from the interface.

- **`vmstat`**
  - **Use Case:** Report virtual memory statistics.
  - **Command:** `vmstat 2`
  - **Example:** Display system performance every 2 seconds.

- **`iostat`**
  - **Use Case:** Report CPU and I/O statistics.
  - **Command:** `iostat -x 2`
  - **Example:** Detailed disk I/O statistics every 2 seconds.

### 2. Disk Management

- **`df`**
  - **Use Case:** Report file system disk space usage.
  - **Command:** `df -h`
  - **Example:** Display disk space in a human-readable format.

- **`du`**
  - **Use Case:** Estimate file space usage.
  - **Command:** `du -sh /var/log`
  - **Example:** Show the size of the `/var/log` directory.

- **`lsblk`**
  - **Use Case:** List information about block devices.
  - **Command:** `lsblk`
  - **Example:** View all attached block storage devices.

### 3. Network Management

- **`ip`**
  - **Use Case:** Show/manipulate routing, devices, policy routing, and tunnels.
  - **Command:** `ip a`
  - **Example:** Display all network interfaces and their IP addresses.

- **`netstat`**
  - **Use Case:** Network statistics, show network connections, routing tables, interface statistics, masquerade connections, and multicast memberships.
  - **Command:** `netstat -tuln`
  - **Example:** Show listening ports and services.

- **`ss`**
  - **Use Case:** Another utility to investigate sockets.
  - **Command:** `ss -tuln`
  - **Example:** Display all listening TCP and UDP ports.

### 4. Process Management

- **`ps`**
  - **Use Case:** Report a snapshot of current processes.
  - **Command:** `ps aux`
  - **Example:** Display all running processes with details.

- **`kill`**
  - **Use Case:** Send a signal to a process, usually to terminate it.
  - **Command:** `kill -9 <PID>`
  - **Example:** Forcefully terminate a process with a specific PID.

- **`pkill`**
  - **Use Case:** Send a signal to processes based on their name or other attributes.
  - **Command:** `pkill -f myapp`
  - **Example:** Kill all processes matching the name "myapp".

### 5. File Management

- **`find`**
  - **Use Case:** Search for files in a directory hierarchy.
  - **Command:** `find /var/log -name "*.log"`
  - **Example:** Find all `.log` files in `/var/log`.

- **`grep`**
  - **Use Case:** Search inside files for matching patterns.
  - **Command:** `grep -r "ERROR" /var/log`
  - **Example:** Recursively search for the keyword "ERROR" in the `/var/log` directory.

- **`rsync`**
  - **Use Case:** Remote file and directory synchronization.
  - **Command:** `rsync -avz /source/ user@remote:/destination/`
  - **Example:** Sync `/source/` directory to a remote destination.

### 6. User Management

- **`useradd`**
  - **Use Case:** Create a new user.
  - **Command:** `sudo useradd -m -s /bin/bash newuser`
  - **Example:** Create a new user `newuser` with a home directory and bash shell.
  
- **`usermod`**
  - **Use Case:** Modify a user account.
  - **Command:** `sudo usermod -aG sudo newuser`
  - **Example:** Add `newuser` to the sudo group.
  
- **`passwd`**
  - **Use Case:** Change user password.
  - **Command:** `sudo passwd newuser`
  - **Example:** Set or update the password for `newuser`.

### 7. Security and Permissions

- **`chmod`**
  - **Use Case:** Change file mode bits.
  - **Command:** `chmod 755 script.sh`
  - **Example:** Set read, write, and execute permissions for the owner, and read and execute permissions for others.
  
- **`chown`**
  - **Use Case:** Change file owner and group.
  - **Command:** `chown user:group file.txt`
  - **Example:** Change the owner of `file.txt` to `user` and the group to `group`.
  
- **`ufw`**
  - **Use Case:** Uncomplicated Firewall, a frontend for managing firewall rules.
  - **Command:** `sudo ufw allow 22`
  - **Example:** Allow SSH traffic through the firewall.

### 8. Package Management

- **`apt`**
  - **Use Case:** Manage packages on Debian-based systems.
  - **Command:** `sudo apt update && sudo apt upgrade -y`
  - **Example:** Update package lists and upgrade all packages.
  
- **`yum`**
  - **Use Case:** Manage packages on Red Hat-based systems.
  - **Command:** `sudo yum update`
  - **Example:** Update all packages to the latest version.
  
- **`snap`**
  - **Use Case:** Install and manage snaps (universal Linux packages).
  - **Command:** `sudo snap install vlc`
  - **Example:** Install VLC media player as a snap package.

### 9. Automation and Scripting

- **`crontab`**
  - **Use Case:** Schedule periodic tasks.
  - **Command:** `crontab -e`
  - **Example:** Edit the crontab file to schedule tasks.
  
- **`ansible`**
  - **Use Case:** Automate configuration management, application deployment, and task automation.
  - **Command:** `ansible-playbook site.yml -i inventory`
  - **Example:** Run an Ansible playbook with the specified inventory file.

### 10. Docker and Kubernetes

- **`docker`**
  - **Use Case:** Manage Docker containers.
  - **Command:** `docker ps -a`
  - **Example:** List all containers (running and stopped).
  
- **`kubectl`**
  - **Use Case:** Control Kubernetes clusters.
  - **Command:** `kubectl get pods`
  - **Example:** List all pods in the current namespace.

---

