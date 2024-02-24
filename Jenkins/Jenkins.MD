## JENKINS

Jenkins is used for Continuous Integration and Continuous Delivery/Deployment (CI/CD).

### CI - Continuous Integration :

It is the combination of Continuous Build and Continuous Test.
  
C.I = C.B + C.T

Build and Test - These Two activities performing in a single task.

**BEFORE C.I :**

![CI Image](https://github.com/naveensilver/Devops/assets/120022254/827fe886-97d6-492e-8d3c-9d4ee95c1240)
  
Multiple developers write the code, and the code is stored in Git Hub Repo.
  
After, we get the source code from git hub and Build the source code in Maven server and Generate Jar/War file.
  
These Jar/War Files tested in another server using Selinium/Junit.
  
If we get any bugs in source code, we can send it back to the developers and the developers fix the bugs/errors and again stored in github.

Note : Each activity performing in different server. So, Manual work is high.
  
  - Build & Test in different servers
  - For Build = Maven/Ant/Gradle
  - For Test = Selenium/JUnit

To Reduce Manual work. We use Jenkins to automate everthing.
  
**AFTER C.I :**
  
![After CI Image](https://github.com/naveensilver/Devops/assets/120022254/b2c4fffb-16b0-478f-a8cf-594703e0830f)

Here, Developers Write the code and store in GitHub Repo.
  
The source code repo is sendeing to CI server.
  
In CI server, The Build and Test will happen automatically.
  
CI Server = Automatic Build + Automatic Test 
  
* CI Server :

Here, The Build, Test and Deploy all the activities are performed in a single CI server.

![CI Server](https://github.com/naveensilver/Devops/assets/120022254/28be9557-d2aa-470d-b3f0-9b4cfa91d4aa)
    
If the code fails in CI server, we can send back to developers and developers fix the bugs.(Repeat Process)
    
Once the code is success, we can deploy the code automatically in CI server.
    
**Benifits Of CI :**
    
Whenever Developers commits code using source code management tool like git, then the CI pipeline gets the Changed codeand runs code automatically. The build and test will be done Automatically.
    
Due to integrating new code with old code. we can esaily know the code is success/failure.
    
Integration - finds the error more quickly.

Developers don't need to do manual tasks.
    
It reduces the developers time 20% - 30%.
    
It delivers product to clients more friquently.
 
### CD - Continuous Delivery/Deployment :
    
* Continuous Delivery :
    
Continuous Delivery is a process, where code changes are automatically built, tested, and prepared for a release to production.  

In Continuous Delivery, Deploy to production - Manually 

* Continuous Deployment :
    
Continuous Deployment is a process, where code changes are automatically built, tested, and deployed to production as soon as they pass the necessary tests in the staging environment. 
    
Ex: Spotify , FacebOOK

In Continuous Deployment, Deploy to production - Automatically. 
   
### Architecture of CI/CD :
    
![Architecture of CI-CD](https://github.com/naveensilver/Devops/assets/120022254/c4f9477f-8855-43a1-abad-d33e292448ab)     
      
**Uses/Benifits/Advanages of CI/CD :**
      
   - automation is more and developers don't need to do manually.
      
   - Improved speed of deployment.
   
   - Improved speed bug fixes.
      
   - Easily roll back code changes.
      
   - Faster product delivery.
      
   - Make early and frequent committments.
      
   - Reduces the developers time 20% to 30%.
      
   - Better Communication.
      
   - Maintainance easy & Tracking easy and update easy.
      
   - Increases Customers satisfaction.
      
   - Reduce the cost.
            
### CI/CD Pipeline :
      
It is one of the most important role for devops engineers.
      
CI/CD Pipeline is a step by step process.
  
It is Combination of multiple Jobs/Tasks.
  
![CI-CD Pipeline](https://github.com/naveensilver/Devops/assets/120022254/34fbd588-41a2-46b2-a00a-74eec067929e)

It's looks like a software developement life cycle(SDLC).
  
Let's consider an example, if you are developing a web application.
   
* Version control : 
  
  Here, developers need to write code for web application. So, it needs to be committed by using Version control system like GIT or SVN.
  
* Build :
  
  let's consider, your code is written in java. it's needs to be compiled before execution. In this build step, code gets compiled and generated .jar file.
  
  Once the build step complited, then move to testing Phase.

* Unit Test : 
  
  It will only test the application components are correctly working or not.
  
  If the unit test is complited, then move to deploy phase.
  
* Deploy :
  
  In this step, we can deploy our code in testing Environment. Here, you can see your application O/p.
  
  Environment : It is setup for our application.
    
  That menans, 
  
    - we need server = EC2-Instance
  
    - Database for storing data = RDS
  
    - For Networking = VPC
  
    - For Storing = S3
  
  Types of Enviroments :
  
  1) DEV = This is for Developers.
  
  2) Q/A = Test Environment - Testers will test the app.
  
  3) Production = This is for Client.
  
* Auto Test :
  
  Once, Our code is working properly in testing server. we need to do automation testing using Selinium/Junit.
  
* Deploy to Production :
  
  If Everything is fine then you can directly deploy your code to Production/Client Server.
  
Note : If we have error in our code then it will give feedback & it will be corrected. if we have errors in Build, it will give feedback & those errors corrected.
  The pipeline will work like until it reaches deploy phase.
  
  Because of this pipeline, Bugs will be reported fast & get reflected. So, entire development is fast.
   
## Jenkins :
  
  Jenkins is an Open Source Project.
  
  Jenkins is written in Java & Developed by Kohsuke Kawaguchi.
  
  Jenkins is Playform independent. (Works on any OS like Windows, Linux, Mac OS)
  
  Jenkins has Community-Supported & Free to use.
  
  Jenkins is first choice for Continuous Integration and It consists of Plugins.
  
  * Plugin is nothing but a small software, that we used to add some extra features to our jenkins dashboard.
  
  Using Plugins, Jenkins Automates the entire SDLC 
  
  #### IMAGE ###
  
  By using single tool, we can intigrate and automate entire software development.
  
  Jenkins was originally developed by Sun Micro-System in 2004 and Named as HUDSON. Hudson was paid software.
  
  After Oracle bought from Sun Micro-System and Renamed as Jenkins and Given for free.
  
  It can run on any playforms without issues.
  
  Whenever developers write the code, we can integrate the code to all developers.
  
  At any point of time, we can Build, Test and Deliver/Deploy application to client. This is Called "CI/CD"
  
  DEV =========> Git ===========> Jenkins =========> Client.
  
  **Advantages :**
  
  Jenkins follows Master-Slave Architecture.
  
  You can write own plugin, can use community plugins also.
  
  Can easily understand the process of what is going on.
  
  **Jenkins Alternatives :**
  
  BamBOO, Travious CI, Circle CI, Git Lab, Buddy, Teamcity, Sema4, AWS code Pipeline.
  
  
  ### MASTER-SLAVE ARCHITECTURE / MASTER ROLES :
  
  Master assign a jobs to the slaves. that slaves works on assigned Job/Work.
  
  If the slaves are not available, master itself done the job.
  
  By using lable, we can specify/assign the job to the nodes/Slaves.
  ```
                               ---> Jenkins Slave-1
                              |     (Windows/Linux)
                              |
  Jenkins-Master -----------------> Jenkins Slave-2
                              |     (Ubuntu/Linux)
                              |
                               ---> Jenkins Slave-3
                                    (Linux/Windows)
  
  ```
	
### Build and Deploymets Process 

1) Take the latest source code from repo

2) Compile Source code

3) Execute Unit Tests (Junits)

4) Perform Code review 

5) Package code as war file

6) Deploy the war file into server

Note : All the above build and deplyments tasks can be automated using Jenkins tool.
  
  ### Jenkins Installation Set-Up :
  
1. Create an EC2 Instnace in Linux (8080 Port Enable) and Connect the instance.
  
2. Update all packages
  
```
  sudo yum update -y 
```
3. Install Java-11 Version (Recommended)
  
```
 sudo amazon-linux-extras install java-openjdk11 -y 
```
4. Install Jenkins (Getting Links from jenkins.io >> Download >> Redhat)
  
  * Add Jenkins Repo to Your Yum Repo and Import the Key file from Jenkins-CI to Enable installation from the package
```
  sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
  sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
```
* Upgrade the service 
```
  sudo yum upgrade 
```
* For Amazon Linux install extra packages #Enterprise edition limited (epel)
```
  sudo amazon-linux-extras install epel -y 
```
* Install jenkins 
```
  sudo yum install jenkins -y 
```
5. Start, Enable and check Status Jenkins service
```
 sudo systemctl start jenkins
 sudo systemctl enable jenkins
 sudo systemctl status jenkins
```
6. Connect Jenkins Dashboard In browser 
  
	>> Ec2-Instance-Public-IP : 8080

Note: Jenkins server running by default 8080 port. Make sure you enabled 8080 port in security group inbound rules which is attached to ec2 instance.

7. Unlock Jenkins and To Get the Initial Administration Password
```
	sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
pwd : 5e5daec716554725b2b1950d728182be

8. Install Suggested Plugins

9. Create First Admin User
  
```
	>> Username :
	>> Password :
	>> Conform Password :
 	>> Full Name:
	>> E-mail address : 
```
10. Instance Configuration 
  
	>> Jenkins URL : http:// ec2-instance-public-ip : 8080

Successfully.. Your Jenkins Is Ready !!
  
### Jenkins Dashboard :
  
1. New Item - To create a job 
2. People - To get no. of Users and User ID's
3. Build History - To get history of build with time and date (Success/Failure)
4. Manage Jenkins >>  
    1. System Config :
        * Configuration System - Configure Global settings and Paths
        * Global Tool config - Configure the tools, their locations and automatic installers. 
        * Manage Plugins - Add, Remove, Enable/Disable Plugins
        * Manage Nodes & Clouds - Add, Remove, Control and Monitor the various nodes that jenkins runs jobs on. (Master-Slave)
    2. Security - To Secure Jenkins 
        * Configure Global Security -Configure who is allowed to use/access System.
        * Manage Credentials - Configure credentials 
        * Configure Credentials Providers - Configure the Credentials providers and types.
        * Manage users - Create/Delete/Modify Users that can log in to this jenkins.
  
    3. Status Info - Build Info, History of jenkins 
    4. Trouble shooting 
    6. Tool & Action - Extra tools shown here 
	
**JOB**
	
Job is nothing but a Task. Job can Build the code, test the code and deploy this code.
	
In Jenkins "New Item" is Used to Create a Job.
	
We have types of jobs in Jenkins :
	
1. Free style project 
2. Pipeline 
3. Multi-configuration project
4. Folder
5. Multibranch Pipeline 
6. Organisation folder 
	

### Create Free-Style Project Job :

1. Go to Jenkins Dashboard 

2. Click on New item 

	>> Enter Item Name 

	>> Select Free Style Project & Click ok

	>> Enter Description 

	>> Click on 'Build' Tab

	>> Click on 'Add Build Step' and select 'Execute Shell'

3. Enter Below Shell-Script >>
```
	touch file.txt
	echo "Hello Babe, welcome to my jenkins classes" >> file.txt
	echo "enjoy padagooww..!!"
```
4. Apply & Save

Note: With above steps we have created Jenkins Job.

5. Click on 'Build Now' to start job execution.

6. Click on 'Build Number' and then click on 'Console Output' to see job execution details.

=> Jenkins Home Directory in EC2 : /var/lib/jenkins/workspace/
		$ cd /var/lib/jenkins/workspace/

7. Go to Jenkins home directory and check for the job name => Check the file created inside the job.

Note : For every minute jenkins job will execute.

### Components of Jenkins :

In Jenkins Job, the terms "general," "source code management," "build triggers," "build environment," "build," and "postbuild actions" refer to various aspects of the software development process that Jenkins facilitates and automates.

Here is a brief overview of what each of these terms means in Jenkins:

1. General: This refers to the basic configuration settings of a Jenkins project, such as the project name, description, and the location of the source code repository.

2. Source code management: This refers to the process of managing the source code for a project, including checking it out from a repository, tracking changes, and merging changes back into the repository.

3. Build Triggers: Build triggers are actions that cause Jenkins to start a build. Jenkins can be configured to start a build automatically when changes are pushed to the repository or on a schedule.

4. Build Environment: The build environment refers to the set of tools and configurations that are used to build the project. This may include setting up the necessary software packages, configuring environment variables, and allocating resources.

5. Build: A build is the process of compiling source code into an executable form. Jenkins can be configured to perform a variety of build types, including compilation, testing, packaging, and deployment.

6. Post-Build Actions: Post-build actions are actions that are performed after the build has completed. These may include sending notifications, archiving artifacts, or publishing reports.

## Build Part : 

Q) Create a Free-Style Job To Automate Build Application Using Jenkins 

**JOB-1 :: JENKINS Job with GITHUB + MAVEN - INTIGRATION [Build App]**

[IMAGE]

Pre-Requisites : Java, Git & Maven 

1. Git installation in Jenkins server 

```
sudo yum install git -y 
```

2. JDK Installation (Java) 

Jenkins Dashboard > Manage Jenkins > Global Tools Configuration > Add JDK > Choose JDK 8 > Configure Oracle Account Credentials

> JDK Name : JDK 1.8 
    
> Version of Java              #We can configure multiple versions of java

> Oracle Login Credentials 

> Save 

* To change specific Java Version:

```
alternatives --config java
``` 

Note: In-order to download Jdk software from the oracle, you need to have a account.

> Go to Browser and search "download java 8 jdk "

> Go to Specific windows version and click on download 

> It will ask Login for Oracle 

3. Install Maven:

Jenkins DashBoard > Manage Jenkins > Global Tool Configuration > Add Maven 

> Name : Maven 3.6

> Version : 3.6.1     #We can configure multiple versions of Maven

> Save 

**Sample Git Repo URL'S For Practice :**

Repo-1 : https://github.com/ashokitschool/JAVA-MAVEN-WEB-APP.git

Repo-2 : https://github.com/ashokitschool/maven-web-app.git


**Steps To Create Jenkins Job With Git + Maven**

1. Connect To Ec2 Instance in which Jenkins Server got installed 

2. Start Jenkins Server

3. Access Jenkins Server Dashboard and Login with your jenkins Credentials.

4. Create Jenkins Job with Git Hub Repo 

	> New Item 

	> Enter Item Name (Job Name) : <passport-app-dev-job>

	> Select 'Free-style Project' & Click Ok

	> Enter Some 'Description' 

	> Go to 'Source Code Management' Tab and select "Git" 

	> Enter Project 'Git Repo URL' (By Default Master Branch will Execute)

	> Add your Github Account Credentials 

	> Go to 'Build' Tab

	> Click On 'Add Build Step' and Select 'Invoke top level Maven Target' 

	> Select 'Maven Version' and Enter Goals 'clean package'

	> Apply & Save 

Note: With Above Steps We have Created Jenkins Job 

5. Click on 'Build Now' to start job execution 

6. Click on 'Build Number' and then click on 'Console Output' to see job execution details.

> Jenkins Home Directory in Ec2 : cd /var/lib/jenkins/workspace/

7. Go to Jenkins workspace and then go to job folder then goto target folder then see war file.

> Today we are worked 'Build Part' only and Tomorrow We are going to work on 'Deployment Part' that means 'Post build actions' 


## Build + Deployment Part :

Q) How to do the deployment into Tomcat Server Using Jenkins ?

Q) How to send a notification to the Development Team by using Jenkins ?

**Job-2 :: JENKINS Job with GITHUB + MAVEN + Tomcat Server - INTIGRATION [Build+Deploy app]**

[IMAGE]

Build + Deployment Job :

1. Developer Push the code in GitHub

2. Clone the Git Repo using Jenkins 

3. Execute the code using maven Goals in Jenkins 

4. Compile the code as war file (JDK) in Jenkins 

5. Deploy War file into Tomcat using Jenkins 

Pre-Requisites :

* Create Ec2 inux VM in AWS Cloud 

* Install Below Softwares in Ec2 Server

> Git 

> Jenkins 

> Tom Cat

* Install Below Software in Jenkins Dashboard Server

> JDK 1.8

> Maven 3.6

> Deploy Container Plugin 

**Steps To Create Jenkins Job With Git + Maven + Tomcat Server**


1. Go to Tomcat Server folder and configure below users in "tomcat-users.xml" file 

```
cd apache-tomcat-9.0.73/
cd conf/
vi tomcat-users.xml
```
Configure below users in 'tomcat-users.xml' file 

```
<role rolename="manager-gui" />
<role rolename="admin-gui" />
<role rolename="manager-script"/>

<user username="tomcat" password="tomcat" roles="manager-gui" />
<user username="admin" password="admin" roles="manager-gui,admin-gui,manager-script"/>

```

To Access the Tomcat Server, change the port num : 9090

```
cd tomcat 
cd conf/
vi server.xml 
```

Giving Access Permissions to All IP Address  (.*)

File Location: <tomcat>/webapps/manager/META-INF/context.xml
```
>>
 <Valve className="org.apache.catalina.valves.RemoteAddrValve"
         allow=".*" />
```
Now start the Tomcat server 
```
cd bin 
./startup.sh 
```
Now Access Tomcat Server :: Ec2_Public_IP : 9090

2. Go to Jenkins Dashboard > Manage Jenkins > Plugins > Search for "Deploy to container" plugin > Install without Restart. 

3. Create a Jenkins Job 

	> New Item 

	> Enter Item Name (Job Name)

	> Select Free-style Project & Click Ok

	> Enter Description 

	> Go to "Source Code Management" tab and Select "Git"

	> Enter Project "Git repo : https://github.com/ashokitschool/maven-web-app.git"

	> Add your Github Account Credentials 

	> Go to "Build" Tab

	> Click on Add Build step and select "Invoke Top Level Maven Targets"

	> Select Maven and Enter Goals "clean package"

	> Click on "Post Build Action" and Select "Deploy war/war to container" option

	> Give Path of war file (you can give like this also **/*.war ) Context Path means "Project Name"

	> Select "Add Container" and Click on "Tomcat 9.x Remote" 

		> Add Tomcat User Permissions (Username: admin, Pwd: admin)

	> TomCat URL = http://13.50.106.153:9090/

	> Apply & Save 

	> Build the Job 

Note: With Above Steps We have Created Jenkins Job 

4. Click on 'Build Now' to start job execution 

5. Click on 'Build Number' and then click on 'Console Output' to see job execution details.

> Jenkins Home Directory in Ec2 : cd /var/lib/jenkins/workspace/

6. Go to Jenkins workspace and then go to job folder then goto target folder then see war file.

Note: If you want to Build + Deployment the Job Automatically

We will use 'Build Triggers' and We can schedule the job using 'cron' syntax.

> Go to Build Trigger and Select 'Poll SCM'

> Schedule " * * * * * " , means schedule the job every minute.

### Build Triggers :

Poll SCM means when you modify the code in the git repository automatically jenkins is going to execute the job. 

Build Periodically : It is like automatic job execution schedule. it will execute the job automatically when the code is changed or not.












## Interview Questions : 

Q) How to stop Jenkins Server in Browser

Access below URL in Browser to stop Jenkins Server.

URL : http://Ec2-IP : 8080/exit 

> 166.56.16.1:8080/exit 

> Click 'Retry using post'

> Shutting Down Automaticaly  

