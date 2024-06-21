# 1.Jenkins Local Setup 

## Install Jenkins Using Docker

### Prerequisites
- Docker installed on your system. If you haven't installed Docker yet, download and install Docker Desktop from the [Docker website](https://www.docker.com/products/docker-desktop).

### Steps to Install Jenkins Using Docker

#### 1. Open Command Prompt or PowerShell
Ensure Docker is running on your system. Open Command Prompt or PowerShell to execute the following commands.

#### 2. Pull the Jenkins Docker Image
Pull the latest Long-Term Support (LTS) version of Jenkins from Docker Hub by running the following command:
```bash
docker pull jenkins/jenkins:lts
```
#### 3. Run the Jenkins Container
Run the Jenkins container using the following command. This command maps port 8080 on your local machine to port 8080 on the container and port 50000 on your local machine to port 50000 on the container, which is used for Jenkins agent connections.

```
docker run -d -p 8080:8080 -p 50000:50000 --name jenkins jenkins/jenkins:lts
```

- `-d`: Run the container in detached mode (in the background).
- `-p 8080:8080`: Map port 8080 on your local machine to port 8080 on the container.
- `-p 50000:50000`: Map port 50000 on your local machine to port 50000 on the container.
- `--name jenkins`: Assign a name to the container.
- `jenkins/jenkins:lts`: Use the Jenkins LTS Docker image.

#### 4. Access Jenkins
Open a web browser and navigate to http://localhost:8080. You should see the Jenkins setup screen.

#### 5. Unlock Jenkins
When you first access Jenkins, you will be asked to unlock it using an initial admin password.

To get the initial admin password, run the following command:
```
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

This command reads the initial admin password from the Jenkins container.

Copy the password from the output of the command and paste it into the Jenkins setup page in your web browser.

#### 6. Customize Jenkins

**6.1.Install Suggested Plugins:**

- After unlocking Jenkins, you will be prompted to install plugins. Choose "Install suggested plugins" for a standard setup.

**6.2.Create First Admin User:**

- Create the first admin user by providing a username, password, and other required information.

**6.3.Configure Instance:**

- Set up Jenkins URL (usually http://localhost:8080).

**6.4.Finish:**

- Complete the setup, and Jenkins will be ready to use.
