Here’s an example of a **Jenkins pipeline** written in **Declarative Pipeline Syntax** for a **Java-based application** using **Docker** as the agent, with stages for workspace cleanup, Git checkout, Maven build, SonarQube analysis, Docker image build and scan, pushing the image to a registry, deployment to **Kubernetes**, and sending notifications:

```groovy
pipeline {
    agent { docker 'maven:3.8.1-jdk-11' }  // Use a Maven Docker image with JDK 11
    
    environment {
        DOCKER_IMAGE = 'my-java-app'       // Name of your Docker image
        REGISTRY_URL = 'docker.io'         // Your Docker registry URL
        REGISTRY_CREDENTIALS = 'docker-credentials' // Jenkins credentials for Docker registry
        SONARQUBE_URL = 'http://sonarqube:9000' // SonarQube server URL
        SONARQUBE_CREDENTIALS = 'sonar-credentials' // SonarQube credentials in Jenkins
        K8S_CREDENTIALS = 'k8s-credentials' // Kubernetes credentials in Jenkins
        K8S_NAMESPACE = 'default' // Kubernetes namespace
        SLACK_CHANNEL = '#ci-notifications' // Slack channel for notifications
    }

    stages {
        stage('Clean Workspace') {
            steps {
                cleanWs()  // Clean the workspace before starting the pipeline
            }
        }

        stage('Checkout Code') {
            steps {
                git 'https://github.com/your-repo/my-java-app.git'  // Replace with your Git repository URL
            }
        }

        stage('Maven Build') {
            steps {
                script {
                    // Run Maven build
                    sh 'mvn clean install -DskipTests=true'
                }
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    // Run SonarQube analysis
                    withSonarQubeEnv('SonarQube') {  // 'SonarQube' is the name of the SonarQube server defined in Jenkins
                        sh 'mvn sonar:sonar -Dsonar.projectKey=my-java-app'  // Adjust for your project key
                    }
                }
            }
        }

        stage('Docker Image Build') {
            steps {
                script {
                    // Build Docker image using the Dockerfile in your repository
                    sh "docker build -t ${REGISTRY_URL}/${DOCKER_IMAGE}:${BUILD_NUMBER} ."
                }
            }
        }

        stage('Docker Image Scan') {
            steps {
                script {
                    // Scan Docker image using a tool like Trivy or Clair (Example for Trivy)
                    sh "trivy image --exit-code 1 --no-progress ${REGISTRY_URL}/${DOCKER_IMAGE}:${BUILD_NUMBER}"
                }
            }
        }

        stage('Push Docker Image to Registry') {
            steps {
                script {
                    // Login to Docker registry
                    withCredentials([usernamePassword(credentialsId: REGISTRY_CREDENTIALS, usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                        sh "docker login -u ${DOCKER_USERNAME} -p ${DOCKER_PASSWORD} ${REGISTRY_URL}"
                    }
                    
                    // Push the Docker image to the registry
                    sh "docker push ${REGISTRY_URL}/${DOCKER_IMAGE}:${BUILD_NUMBER}"
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                script {
                    // Use kubectl to deploy the Docker image to Kubernetes
                    withCredentials([kubeconfigFile(credentialsId: K8S_CREDENTIALS, variable: 'KUBE_CONFIG')]) {
                        sh "kubectl --kubeconfig=${KUBE_CONFIG} set image deployment/my-java-app my-java-app=${REGISTRY_URL}/${DOCKER_IMAGE}:${BUILD_NUMBER} --namespace=${K8S_NAMESPACE}"
                        sh "kubectl --kubeconfig=${KUBE_CONFIG} rollout status deployment/my-java-app --namespace=${K8S_NAMESPACE}"
                    }
                }
            }
        }
        
        stage('Notify Slack') {
            steps {
                script {
                    // Send a notification to Slack about the build status
                    def buildStatus = currentBuild.result ?: 'SUCCESS'
                    slackSend(channel: SLACK_CHANNEL, message: "Build ${buildStatus}: ${env.JOB_NAME} ${env.BUILD_NUMBER} - ${currentBuild.url}")
                }
            }
        }
    }

    post {
        always {
            // Clean up Docker images to free resources
            sh 'docker system prune -af'
        }
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build or deployment failed. Please check the logs for details.'
        }
    }
}
```

### **Explanation of the Pipeline:**

1. **Agent:** The pipeline uses the **Maven Docker image** (`maven:3.8.1-jdk-11`) to run all the stages. You can adjust this based on the version of Maven and Java you’re using.

2. **Environment Variables:**
   - `DOCKER_IMAGE` is the name of the Docker image.
   - `REGISTRY_URL` is the Docker registry URL.
   - `SONARQUBE_URL` and `SONARQUBE_CREDENTIALS` represent the URL and credentials for SonarQube integration.
   - `K8S_CREDENTIALS` and `K8S_NAMESPACE` are used for Kubernetes deployment.
   - `SLACK_CHANNEL` is the channel where notifications will be sent.

3. **Stages:**
   - **Clean Workspace:** Cleans the Jenkins workspace before starting.
   - **Checkout Code:** Checks out the code from your Git repository.
   - **Maven Build:** Runs Maven to build the Java application (`mvn clean install`), skipping tests during the build.
   - **SonarQube Analysis:** Runs SonarQube analysis using the `mvn sonar:sonar` command.
   - **Docker Image Build:** Builds a Docker image using the Dockerfile in the repository.
   - **Docker Image Scan:** Scans the built Docker image for vulnerabilities using **Trivy** (you can replace this with any image scanning tool).
   - **Push Docker Image to Registry:** Logs in to the Docker registry and pushes the Docker image.
   - **Deploy to Kubernetes:** Deploys the Docker image to a Kubernetes cluster using `kubectl`.
   - **Notify Slack:** Sends a notification to a Slack channel about the build status.

4. **Post Actions:**
   - **Always:** Cleans up unused Docker resources using `docker system prune`.
   - **Success/Failure:** Custom success and failure messages.

### **Customization:**
- Replace `my-java-app`, `docker.io`, `http://sonarqube:9000`, and other placeholders with your actual project and environment details.
- Ensure the credentials for Docker, SonarQube, and Kubernetes are set up in Jenkins and referenced correctly using `credentialsId`.

This pipeline automates the process of building, scanning, and deploying a Java-based application using Docker and Kubernetes while integrating with SonarQube for code quality and providing notifications via Slack.
