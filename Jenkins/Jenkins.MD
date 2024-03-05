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
  
  [IMAGE]
  
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

  Master assign a jobs to the slaves. That slaves works on assigned Job/Work.
  
  If the slaves are not available, Master itself done the job.
  
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
  
1. Create an EC2 Instnace in Linux (Custom TCP + 8080 Port Enable) and Connect the instance.
  
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
* For Amazon Linux install extra packages #Extra Packages for Enterprise Linux (epel)
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

Q) How to know/Change the single tool multiple versions in one server.

Explanation : For Ex, if you have 2 java versions in single server (Java11 and Java-1.8.0)

To check Change the versions of single tool. we use command 

```
	update-alternatives --config java
```
Here, we will get the versions list of single tool and by entering the version S.No we can re-install the specific version.
  
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
	
# 1. Free-Style Project Job Creation :

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

   Here, We Can See 'BUILD HISTORY' with 'Build Number'.

```
	#1 Blue Colour   --->  Process
	#1 Green Colour  ---> Success
	#1 Red Colour    ---> Failed
	#1 Black Colour  ---> Abort/Cancel
	#1 Orange Colour ---> Pending
```

6. Click on 'Build Number' and then click on 'Console Output' to see job execution details.

   Here, We can see the output of jenkins job in Console output.

7. Go to Jenkins home directory and check for the job name => Check the file created inside the job.

   Jenkins Home Directory in EC2 : /var/lib/jenkins/workspace/
```
	cd /var/lib/jenkins/workspace/
```

Note : Whenever you create and build a job. workspace folder will be created in Linux server as well as Jenkins server.

- Linux server  ```cd /var/lib/Jenkins/workspace/job-1 ```

- Jenkins server  dashboard > job > workspace > console output > history of Jenkins 

   Here, We will get the output of Jenkins job.

### Components of Jenkins :

In Jenkins Job, the terms "general," "source code management," "build triggers," "build environment," "build," and "postbuild actions" refer to various aspects of the software development process that Jenkins facilitates and automates.

Here is a brief overview of what each of these terms means in Jenkins:

1. General: This refers to the basic configuration settings of a Jenkins project, such as the project name, description, and the location of the source code repository.

2. Source code management: This refers to the process of managing the source code for a project, including checking it out from a repository, tracking changes, and merging changes back into the repository.

3. Build Triggers: Build triggers are actions that cause Jenkins to start a build. Jenkins can be configured to start a build automatically when changes are pushed to the repository or on a schedule.

4. Build Environment: The build environment refers to the set of tools and configurations that are used to build the project. This may include setting up the necessary software packages, configuring environment variables, and allocating resources.

5. Build: A build is the process of compiling source code into an executable form. Jenkins can be configured to perform a variety of build types, including compilation, testing, packaging, and deployment.

6. Post-Build Actions: Post-build actions are actions that are performed after the build has completed. These may include sending notifications, archiving artifacts, or publishing reports.

## Dashboard > Job > Configuration 

1. General :

* Discard Old Builds - Used To Delete the Previous Build automatically.

	> Strategy : Log Rotation

	> Days to keep builds : 10 

	> Max # of Build Keep : 10 (it keeps the latest 10 builds and delete the old builds)

* GitHub Project :

	> Project URL : Git Hub Link 

* This Project is Parameterised :

> i) Boolean Parameterised - Used in True/False Condition

	> Name : Jenkins 

	> Set by default - yes 

	> Description - Jenkins is in Active

	> Save and Click on Build with Paramters 

	> Build

> ii) Choice Parameters - When you have multiple branches but you want to build single branch at the time we use Choice Parameter.

	> Name : Branches 

	> Choices : Master Main Branch1 Branch2 

	> Save and Click On Build With Paramters 

	> Select Particular Branch and Build.

> iii) Credential Parameter - Whenever you want to intigrate the tools with jenkins like Ansible, Docker, Tomacat..

	> User name & Password 

> iv) File Parameter - If the Build Files are Present in Local System (Laptop)

	> File Location - DevOps\Ashok IT\DevOps PlayList

	> Save & Build with Parameters 

	> Select Files and Builds 

	> To check the Build Output : cd /var/lib/jenkins/workspace/jobs/DevOps/Ashok IT/DevOps PlayList

> v) String Parameter - When you want to pass the information while Build.(Single line)

	> Name : User Name 

	> Default Value : Naveen

	> Description: Here i Provided my details 

	> Build with parameters 

> vi) Multi-String Parameter - When you want to pass the multiple info while build. (Multi line)

	> Name : User Name 

	> Default Value : Naveen | Silver | i am Devops engineer

	> Description: Here i Provided my details 

	> Build with parameters 

> vii) Password Parameter - It is similar to Credential Parameter.

> vii) Run Parameter - When you want to run the script that time we use Run Parameter.

* Throttle Builds:

* Execute Concurrent Builds if Necessary

2. Source code management :

* None 

* Git 

> Repo URL :

> Credentials : 	+(Add)

Note : If you want use Bit Bucket Repo, we need to install Bit Bucket Plugin.

3. Build Triggers :

* Build Periodically - Used to Automate Build Schedule. Here, we use Cron Syntax " * * * * * "

### CRON Syntax :
```
It has 5-Stars, Each star has single space.

	> 1st * Represents Minutes.
	> 2nd * Represents Hours (24 hrs)
	> 3rd * Represents Day of the Month (31)
	> 4th * Represents Month
	> 5th * Represents Day of the Week (7) [Sunday=0 to Saturday=7]

```
Cron Website : https://crontab.guru/

Ex1: 28 Dec 7:45AM WED - Cron Syntax is " 45 7 28 12 3 "

Ex2: " * * * * * " Means Build the Job at Every Minute. 

Note: If you want to stop the build automation, we have to Remove the Cron Syntax.

* Poll SCM - Source Code Management - Build the Job in Particular Day & Particular Time 

Here, When the changes happens, it will Build Automatically in a Particular Time.

Scenario, When the Developer changes the code. It will build the job automatically at a particular time.

Q) Diff B/w Build Periodically and Poll SCM 

Poll SCM : It will Builds the job automatically when the changes done by developer at a particular time.

Build Periodically : It is like automatic job execution schedule. it will execute the job automatically when the code is changed or not.

* Build After Other Project Are Built - Which is Used in Pipeline Jobs.

It will build the job when the other job is executed. (Upstream and Downstream)

	> Trigger Only Build is stable - It will build the Job, when upstream Job is Success.

	> Tigger even if the build is unstable - It will Build the Job, When the Upstream Job is in Unstable either success or failure.

	> Trigger if the build fails - It will Build the Job, when the Upstream Job Fails.

	> Always Trigger, Even the build aborted - Cancel the Build

* Webhook trigger for GITScm Polling


4. Build Environment:

5. Build Steps:

> i) Execute Shell - Used to Run Commands 

	> Here, We can create file/folder,delete file/folder,Print data...etc.


6. Post-Build Actions:

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

## Dashboard > Job
```
>> Status - Job Status 
>> Changes - Job Changes 
>> Workspace - We can see Job Output & We can download the output files and we can delete entire workspace files.
>> Build Now - Build the job
>> Cofigure - We can made the job changes again.
>> Delete Project - Delete the job
>> GitHub - 
>> Rename - To Rename job
```

## Dashboard > Job > #1

```
>> Status - Build Status 
>> Change - Build Changes
>> Console O/p - History of Job/Build
	> view as Plain - Console output in plain text.
>> Edit Build Infp - Rename Build Name 
>> Delete Build - Delete Build
```

### Create a Free-Style Job to Get Code From GitHub Private Repo

1. Go to Jenkins Dashboard > Enter Item Name > Freestyle project > ok

- General :
    - GitHub Project : [GitHub_Private_Repo_URL]

- Source Code Management :
    - Git : Repo URL : [GitHub_Private_Repo_URL]

    Note : Make sure Git should be installed in your server.

    - Credentials : + Add
        - Kind : Username with Password 
        - Username : naveensilver [Your_GitHub_userName]
        - Password : Generate GitHub Token(ref.2) [Paste_GitHub_Token]
    - Branches to Build : */master 

    Note: Given Branch should Present in Github Repo

    - Save and Build the Job 

2. Steps To Generate GitHub Token 

- In GitHub > Settings > Developer settings > Personal Access tokens > Token (classic)

    - Generate New Token > Note: My-Jenkins-Token > Select Scopes: Repo > Generate Token > Copy Token 

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

## Jenkins Pipeline Using Free style Project Job :

The Sequence of jobs execution is called as "Pipeline".

For our application we will use multiple environments like below 

> DEV 

> SIT 

> UAT 

> PILOT 

> PROD 

For every environment, one job will be created.

> JENKINS_DEV_JOB ----------> DEV Environmet (Dev Server)

> JENKINS_SIT_JOB -----------> SIT Environmet (SIT Server)
	
> JENKINS_UAT_JOB ----------> UAT Environmet (UAT Server)

> JENKINS_PILOT_JOB --------> PILOT Environmet (Pilot Server)

> JENKINS_PROD_JOB --------> PROD Environmet (Prod Server)

If we want to deploy code changes to all environmets then it is recommended to create Build pipeline.

By using Build pipeline, we can execute Jenkins Jobs Sequentially.

Note: Instead of executing each job manually, we can create Build pipeline. So, we can execute jobs automatically.

PIPELINE-Task :
=============

If Code commit happend in github then deploy code into DEV server.

If Dev Server Deploy successful, then deploy code into SIT Environment.

If SIT deployments successful, then deploy code into UAT environment.

Steps to Configure Jobs and Execute Jobs In Sequences
------------------------------------------------------

1. Create Ec2 VM and install Tomcat Server (Dev Server)
	> Connect Dev Instance and Access the Dev Tomcat Server

2. Create Ec2 VM and install Tomcat Server (SIT Server)
	> Connect Dev Instance and Access the Dev Tomcat Server

3. Create Ec2 VM and install Tomcat Server (UAT Server)
	> Connect Dev Instance and Access the Dev Tomcat Server

4. Create Ec2 VM and install Jenkins

5. Install Jdk, Maven, Git, Deploy to container plugin and Build Pipeline Plugin in Jenkins Server

6. Create Jobs in Jenkins Server

	i) DEV-Job --------------> Dev Server

	> Create a "Dev_Job" Using Free-sytle Project

	> General, Enter Description "Dev-Job"

	> Go to SCM, Select Git and Enter Repo URL

	> Build Trigger, Click on Poll SCM and Schedule " * * * * * " (Every min, it is going to check the repo)

 	> Build Environment, Select "Delete work space before build starts"

	> Build Steps, Select "Invoke top-level Maven Targets" and Enter Goal "clean package"

	> Post Build Action, Select "Deploy War/ear to container" and Give war file path "**/*.war" #"Deploy to container" Plugin must be installed. 

	> Context Path "Dev-Project-Web"

		> Add Container "Tomcat 9.x"

		> Paste Dev-Tomcat Server URL : http://54.556.664.45:8080/

	> Apply & Save.

	ii) SIT-Job  --------------> SIT Server  (SIT-Job should execute if DEV-Job is stable )

	> Create a SIT_Job Using Free-sytle Project
	
	> General, Enter Description "SIT-Job"
	
	> Go to SCM, Select Git and Enter "Repo URL"
	
	> Build Trigger, Select "Build after other Project are build"

		> Project to watch " Dev_Job" 

		> Select 'Tigger only if build is stable"

	> Build Environment, Select "Delete work space before build starts"
	
	> Build Steps, Select "Invoke top-level Maven Targets" and Enter Goal "clean Package"
	
	> Post Build Action, Select "Deploy War/ear to container" and Give war file path "**/*.war"
	
	> Context Path "SIT-Project-Web"
		
		> Add Container "Tomcat 9.x"
		
		> Paste SIT-Tomcat Server URL : http://54.556.664.46:8080/
	
	> Apply & Save.

	iii) UAT-Job---------------> UAT Server (UAT-Job should execute if SIT-Job is stable )

	> Create a "UAT_Job" Using "Free-sytle Project"

	> General, Enter Description "UAT-Job"
	
	> Go to SCM, Select Git and Enter "Repo URL"
	
	> Build Trigger, Select "Build after other Project are build"
		
		> Project to watch " SIT_Job" 

		> Select 'Tigger only if build is stable"

	> Build Environment, Select "Delete work space before build starts"
	
	> Build Steps, Select "Invoke top-level Maven Targets" and Enter Goal "clean Package"
	
	> Post Build Action, Select "Deploy War/ear to container" and Give war file path "**/*.war"

	> Context Path "UAT-Project-Web"

		> Add Container "Tomcat 9.x"
		
		> Paste UAT-Tomcat Server URL : http://54.556.664.47:8080/

	> Apply & Save.

> Go to Jenkins Dashboard, we can see 3 Jobs Created.

> Now we need to execute these jobs through a pipeline automatically.

7. Create Jenkins Build Pipeline to Execute the jobs in jenkins.

	> Install "Build Pipeline" plugin

	> Go to Jenkins Dashboard, we can see new "+" icon, on top of jobs.

	> Click on "+" icon, Enter Name "My-Pipeline" and Select "Build Pipeline View" and Click on "Create"

	> Description "My Project pipeline"

	> Build Pipeline View Title "My Pipeline-Project"

	> Pipeline flow, Layout "Based On up/down stream relationship"

	> Upstream/Downstream Config, Select initial Job "Dev_Job"

	> Apply & Save.

8. Go To Build Pipeline View

	> Tigger pipeline, it will execute the dev_Job. now go and check in dev tomcat server. we can see application is deployed.

	> Automatically, SIT and UAT jobs will be executed in sequence.

9. Now, Modify the data in Git-Repo and automatically Job should execute after 1min.

Q) If we forgot Jenkins Password, then how to recover it ?

First Stop Jenkins Server ```systemctl stop jenkins```

> Go to /var/lib/jenkins/config.xml

> Set value for useSecurity as false 
	
	Ex: <useSecurity> false </useSecuirty>

> Re-start Jenkins & Try To Access.

Q) How To change Jenkins Port Number?

> Go to Root Directory

> Go to ```/etc/sysconfig```

> open jenkins file and Change Port Number ```sudo vi jenkins```

> JENKINS_PORT="8080"

> Restart Jenkins Server. 

Q) How can we deploy code into server from a particular branch.

> Using "Project is Parameterized"

> Choice Paramter is if u want to enter branch names automatically.

> String Parameter is if u want to enter branch names manually.

Note: During Job Excution, we can select a particular branch and we can execute that branch only

Job Parameterised-Task :
=======================

Q) Create a Job and Execute the job using "Job Parameterized"

> Create a Job using Free-style project

	> General, Select "this Project is Parameterized" and Add peramter "Choice Paramter"

		> Name : BranchName 

		> Choices : Enter Every Branch Name in nextline

		> Description : BranchName

	> SCM, Select Git and Enter Repo URL.

		> Branches to Build :  */${BranchName}  #configure branch name dinamically.

	> Build Trigger, Poll SCM " * * * * * "

	> Build Environment, Select "Delete work space before build starts"

	> Build Steps, Select "Invoke top-level Maven Targets" and Enter Goal "clean Package"

	> Post Build Action, Select "Deploy War/ear to container" and Give war file path "**/*.war"

	> Context Path "SIT-Project-Web"

		> Add Container "Tomcat 9.x"

		> Paste SIT-Tomcat Server URL : http://54.556.664.46:8080/

	> Apply & Save.

> Inside the Job, we can See "Build with Paramter" Option and Click it.

	> Select the "Branch" Name and "Build" it 

Note : If the selected branch is not available in Git repo, the Build will gets "Fail"

> Go to Tomcat and check the Application


## Users & Roles in Jenkins

In a Project, all the team members should have jenkins access.

DevOps Team members will use jenkins to create jenkins jobs for build and deployment automation.

Dev & Testing team member will use jenkins to run the jobs.

Note : So, We can call jenkins is role based application.

Exercise :
----------
Create 1 account for DevOps Team and Give all Permissions.

Create 1 account for Dev team and Give only "Overall" read and "Job" Build permissions.

Create 1 account for Test team and Give only "Overall" read and "Job" Build permissions.

Create Users In jenkins
------------------------

1. Go to Manage Jenkins > security >> Manage users

> Create User (Devops)

	> username : devops_user
	> password : 123
	> confirm pwd : 123
	> Devops
	> silver@gmail.com
	> Create User

> Create user (Dev)

	> username : dev_user
	> password : 123
	> confirm pwd : 123
	> Developer
	> dev@gmail.com
	> Create User

> Create user (Test)

	> username : test_user
	> password : 123
	> confirm pwd : 123
	> Tester
	> test@gmail.com
	> Create User

2. Go to /var/lib/jenkins/users/users.xml file (you can see user accounts created)

Note: Devops teams members should do all Operations activities in Jenkins where as Dev and test Teams have permissions to "only runs the job" in real time. so, we can configure permissions for users.

3. Go to Manage Jenkins > Security >> Configure Global Security (User Permission)

> Authentication

	> Security Realm
		> Jenkins own user database (Select)
		> LDAP (Company specific-All the employe server details in LDAP server)

	> Authorization 
		> Project Based Matrix Autorization Strategy / Matrix Based Security / Role-Based Strategy

Here, We can Manages Users Permission in Different Ways 

Case-1) Using "Matrix Based Security". We will get User/Group Box and we can add Users/Groups directly.

	> Click On Add user and user name "devops_user" 
		> For Devops user, i will give Overall "Administer" Permissions.

	> Click On Add user and user name "dev_user" 
		> For Dev user, i will give Overall "Read" and Job "build and Read" Permissions.

	> Click On Add user and user name "test_user" 
		> For Test user, i will give Overall "Read" and Job "build and Read" Permissions.

> Also we can add "Groups"

Case-2) Using "Role-Based Strategy". 

Go To Jenkins Dashboard > Manage Jenkins > System Configuration > Manage Plugins > Available Plugins 

Search "Role-Based Authorization Strategy". Select and Install Without Restart.

Now Create 3 User like DevOps_user, Dev_user, Test_User.

Go to Dashboard > Manage Jenkins > Security 

Then, We get a New Options "Manage and Assign Roles"

> Manage and Assign Roles

	> Go to Manage Roles 

		- Role to add : DevOps_Role > Click on "Add" and Give Admin Permissions

		- Role to add : Dev_Role > Click on "Add" and Give Perticular Permissions like Read all 

		- Role to add : Test_Role > Click on "Add" and Give Particular Permissions

		- Then Save.

	> Assign Roles 
		
		- User/Group to add : DevOps_user and Click on "Add" and Select Global Role as "DevOps_Role"

		- User/Group to add : Dev_user and Click on "Add" and Select Global Role as "Dev_Role"

		- User/Group to add : Test_user and Click on "Add" and Select Global Role as "Test_Role" 
		
		- Then Save 

Note: Log-out from Admin account and Log-in using Above DevOps, Dev, Test team Credentials.

Q) Diff B/w Authentication & Authorization

Authentication means who can login into our application.

Authorization means once they login what the users can do in application

# MASTER & SLAVE

Q) Why Jenkins Master & Slave Configurations ? 

When we build the jobs in a single jenkins master node then jenkins uses the resource of the base machine and if no executor is available then the jobs are queued in jenkins server.

Sometimes you might need several different environments to test your builds. this cannot be done by a single jenkins server.

It is recommended not to run different jobs in the same system that required a different environment. In such scenarios where we need a different machine with different environmet that takes the specific job from the master to build.

On the same jenkins setup, multiple teams are working with their jobs. all jobs are running on same base operating system and the base operating system has limited resources.

To overcome this problem, jenkins provided Distributed Architecture. i.e Jenkins Master-Slave Architecture.

(OR)

Q) Why we need to go for Master-Slave config ? (IMPORTANT)

In realtime, we can take jenkins s/w in one machine and we can create the jobs in that jenkins. if we run multiple jobs at a time then burden will be increased on jenkins machine. 

So, To Reduce the burden on jenkins we are going to use master and slave architecture.

No need to install the Jenkins S/W in every slave machine, just we will install JVM (Java) i.e, Jenkins Dependency is JAVA.

## Master-Slave Architecture :

Jenkins uses a Master-Slave Architecture to manage distributed builds. the machine where we install jenkins software will be jenkins master and that run's on port 8080 by default. 

On the slave machine, we install a program called Agent. This agent requires JVM. This Agent executes the tasks provided by Jenkins Master.

The Jenkins jobs created on Jenkins Master and Jenkins Jobs execution will happen in Slave machine.

We can launch 'N' no. of agents and we can configure which task will be run on which agent server from jenkins master by assigning the agent to the task.

### Jenkins Master

Your main Jenkins Server is the Master. the master's job is to handle:

a) Scheduling build jobs.

b) Dispatching builds to the slaves for the actual execution.

c) Monitor the slaves (Possibly taking them online and offline as required).

d) Recording and Presenting the build results.

e) A master instance of jenkins can also execute build jobs directly.

### Jenkins Slave

A slave is a java executable that runs on remote machine. Following are the characteristics of jenkins slave:

a) It hears request from the jenkins master instance.

b) Slaves can run on variety of Operating systems.

c) The job of slave is to do as they told to, which involves executing build jobs dispached by the master.

d) You can configure a project to always run on a particular slave machine or a particular type of slave machine , or simply let jenkins pick the next slave available.

Advantages :

-- Work load is Destributed.

-- Faster Execution.

-- Deployment Faster.

### Working With Master-Slave Architecture


Step-1 : Create Jenkins Master

1) Create Ec2 Instance With Key-Pair(.Pem)
2) Connect Ec2 Using Mobaxterm 
3) Install Git Client  $ sudo yum install git -y 
4) Install Java S/w  $ sudo yum install java-1.8.0-openjdk -y 
5) Install Jenkins Server
6) Add Git, JDK, Maven Plugins.
7) Enable Jenkins Port No. in Security Groups
8) Access Jenkins Server in Browser and Login.


Step-2 : Create Jenkins Slave

1) Create Ec2 Instance 
2) Connect Ec2 Using Mobaxterm 
3) Install Git Client  $ sudo yum install git -y 
4) Install Java S/w  $ sudo yum install java-1.8.0-openjdk -y 
5) Create one directory in /home/ec2-user (ex: slavenode)


Step-3 : Configure Slave Node in Jenkins Master Node Server

> Go to Jenkins Dashboard 

> Go To Manage Jenkins 

> Go to Manage Node & Clouds 

> Click on 'New Node', Enter Node Name and select 'Permanent Agent'

> No. of executors : 1

Note: if u want to run 3 jobs at a time, you can take 3 executors.

> Enter Remote Root Directory (/home/ec2-user/slavenode)

> Enter Label name as 'Slave-1'

> Usage "Use this node as much as possible"

> Select Launch Method as 'Launch Agents Via SSH'

	> Give Host as 'Slave VM Public DNS URL' Ex: ec2-3-110-223-251.ap-souch-1.compute.amazonaws.com (Or) Slave Private IP
	
	> Add Credentials (select kind as : SSH username with Private key)
	
	> Enter Username as : ec2-user 
	
	> Select Private as Enter directory and add private key.

Note: Open Gitbash From your .pem file location and execute below command to get private key from pem file 

	$ cat <key-pair-file-name>.pem

	> It will display private key on gitbash terminal (Copy and Paste in Jenkins)

> Select Host key strategy as 'Manually trusted key Varification Strategy'/ 'Keep this agent online as much as possible' 

> Click on Apply & Save (we can see configure slave)

> Successfully slave-1 is created 

> With Above steps Master-Slave Configurations Completed.

Step-4 : Create Job and Execute

> Go to Jenkins Server and Create a Job

> Go to "General" Sections in Jenkins Job

> Select 'Restict where this project can be run'

Note: If you will not select this option, Jenkins Job will be excuted in Master node' Path: /var/lib/jenkins/workspace/[Jobname]

	> Label Expression : slave-1

> Configure the Remaining Sections (Scm, Build triggers, build, post-build actions)

> Build the Job and the Job will executed on slave node.

> Check the console output and We can see Build slave Path : /home/ec2-user/slavenode/workspace/[jobname]

> Go slave server and check the excution Output 

 Note: Using Master and Slave, we can also execute in Master as well as slave server.

==========================

## BACK UP In Jenkins :

Q) How to take Backup Jenkins Server files In Jenkins.

In Jenkins, We will Back up the Build Job Info for further Purposes. 

We Install "Thin Backup" Plugin. Used to Backup the deleted data in Main Server. We Create No. of Backupp Folder.

Go To Jenkins Dashboard > Manage Jenkins > Manage Plugins > Available Plugins > Search "ThinBackup" and Install without Restart.

Go To Dashboard > Manage Jenkins > Tools and Actions > ThinBackup > Go to Settings > ThinBackup Configurations 

> Backup Directory : ```/opt/jenkins/backup```

Note: Create a Backup folder and it should have Read, Write, Execute Permissions and also should have Jenkins:Jenkins (User:Group) Permissions.

- To change permission we use ```chmod -R 777 jenkins``` 

- To Change user:group Permissions ```chown jenkins:jenkins jenkins```

- To Check List of users :  ```cat /etc/passwd```

Go Back to ThinBackup Configurations

> Backup schedule for full backups : 30 14 * * * (Cron Syntax)

> Max num of backup sets: -1 

> Backup Build Results : select all and Save.

Now Go To Dashboard > Manage Jenkins > Tools and Actions > ThinBackup

Click on "Backup Now". Automatically Backup file will be created in Backup Directory.

Now, Go to ```/var/lib/jenkins```, delete any files and try to restore it.

Go to ThinBackup > Click on "Restore". Select restore backup file and Restore.

Check the files restored or not in ```/var/lib/jenkins```.

Q) How to Install Jenkins using File 

Create ```vim jenkins.sh``` and store all Jenkins installation commands in this file.

This file should have executable permissions : ```chmod +x jenkins.sh ```

Now, Execute the file ```./jenkins.sh ```

Jenkins will install automatically. 

check the jenkins server ```systemctl status jenkins```



# 2. Pipeline Job :

Jenkins Pipeline is a combination of plugins which automates no. of tasks and makes CI/CD pipeline effiecient, high in Quality and reliable.

Jenkins pipeline is automation solution that let's you create simple or complex pipelines.

A Pipeline is a group of stages interlinked with eachother in a sequence.

Jenkins provides two ways of developing a pipeline

1) Scripted 

2) Declarative 

Generally, Jenkins jobs were created using Jenkins UI called Jenkins Free-style jobs.

In Jenkins 2.0, Jenkins introduced a way to create jobs using the technique called pipeline as code.

In Pipeline as code technique, jobs are created using a script file that contains the steps to be executed by the job.

In Jenkins, that scripted file is called Jenkinsfile.

## What is Jenkinsfile

Jenkinsfile is nothing but a sample text file which is used To write the Jenkins Pipeline and To automate the contineous integration process.

Jenkinsfile is usually checked in along with the project source code in Git repo. Ideally, every application will have it's own Jenkinsfile.

Jenkins can be written in two ways.

1) Scripted Pipeline syntax
2) Declarative Pipeline syntax 

NEW ITEM > NAME > PIPELINE > SAVE 

### 1. What is Scripted Pipeline ?

Jenkins pipeline are generally written as scipted pipelines. ideally, the scripted pipelines stored in jenkins web UI as a Jenkinsfile.

The end-to-end scripted pipeline script is written in Groovy.

It requires knowledge of Groovy Programming as a pre-requisites.

If you, use scripted pipeline, you need to know any programming language like Groovy, python.

Jenkinsfile start with the word 'node'.

It can contains standard programming constructs like if-else block, try-catch block etc.

- Sample Scripted Pipeline 

```
node {
    stage("Stage-1){
        echo "hai"
    }

    stage("stage-2"){
        echo "hello"
    }
}

```
### 2. What is Declarative Pipeline?

The Declarative Pipeline sub-system in jenkins pipeline is relatively new, and provided a simplified, opinionated syntax on top the Pipeline subsystems.

The latest addition in Jenkins Pipeline job creation technique.

Jenkins declarative pipeline needs to use the predefined constructs to create pipelines. Hence it is not flexible as a scripted pipeline.

Jenkinsfile starts with the word 'pipeline'

Jenkins declarative pipeline should be the preferred way to create a jenkins job as they offer a rich set of features, come with less learning curve & no pre-requisite to learn a programming language like Groovy just for the sake of writting pipeline code.

If you use declarative pipeline, you no need to know any programming language.

We can also validate the syntax of the Declarative pipeline code before running the job. it helps to avoid a lot of run time issues with build script.

### Declarative Pipeline Architecture : 
<Image>

Pipeline : Entire Declarative pipeline script should be written inside the pipeline block. It's a mandatory block.

Agent : Specify where the jenkins build job should run. agent can be at pipeline level or stage level. it's mandatory to define an agent.

Stages : Stages block contains diff executable stage blocks. at least one stage block is mandatory inside stages block.

Stage : Stage block contains the actual execution steps. Stage block has to defined within stages block. it's mandatory to have at least one stage block inside the stages block. also its mandatory to name each stage block & this name will be Unique.

Every stage block is having single steps block. inside steps block we will give commands or scripts.

- Sample Declarative Pipeline

```
Pipeline {
    agant any  // any means which server is available. In that server build the job
    stages {
        stage("Stage-1") {
            steps {
                echo 'Hello World'
            }
        }
    }
}

```
Q) Write a multi stage pipeline 

```
pipeline {
    agent any
    stages {
        stage("code") {
            steps {
                echo "Code is done"
            }
        }
        stage("build"){
            steps{
                echo "Build is done"
            }
        }
        stage("test"){
            steps{
                echo "Test is done"
            }
        }
        stage("deploy"){
            steps{
                echo "Deploy is done" // echo is used to print the text.
            }
        }
    }
}

```
Note : If any stage is failed and the next stage will be failed/stopped.

Q) Write a pipeline to execute the commands.

```
Pipeline {
    agant any  
    stages {
        stage("File") {
            steps {
                sh "touch myfile.txt" // sh is used to execute command
                sh "date"  
                sh "mkdir myfolder"
            }                         // single 'sh' with multiple commands
            steps {
                sh '''
                touch flm.png
                mkdir folder
                date 
                cal
                '''
            }
        }
    }
}

```

We can check the output in server "/var/lib/jenkins/workspace/[JobName]"

Q) Write a pipeline to Execute the job in Dev-Slave node

-- First Create 2 Ec2 Instances (MasterNode, SlaveNode)

- Set Jenkins server in Master Node.

- Install Jenkins Dependency(java) in Slave Node.

- Set up an Agent(Slave Node) in Jenkins Dashboard 

> Jenkins Dashboard > Setup an agent/Manage Nodes and Clouds

    > New node name : node1 , type : Permanent Agent and Create

    > Name : node1
    > Description : This is for dev_slave
    > Number of executers : 2
    > Remote root directory : /home/ex2-user/jenkins/ 
    > Labels : dev
    > Usage : Only build jobs with label expressions matching this node
    > Lunch Method : Lunch agent via SSH
        > Host : Slave-Node_Private_IP
        > Credentials : +Add 
            > Add Credentials : 
                > Kind : SSH Username with Private key
                > Description : This is for Slave Node
                > Username : ec2-user
                > Private key : select "Enter directly" and paste .pem file data.
            > Host key Verification strategy : Non Verifying Strategy
            > Availability : keep this agent online as much as possible
            > Save and node1 will be created

Go to Dashboard > Job > Configure > Pipeline Script

```
Pipeline {
    agant {
        label 'dev'
    }
    stages {
        stage("Stage-1") {
            steps {
                echo 'Hello World'
            }
        }
    }
}

// Save and Build Job

// Check Console output and Varify path in Dev-Slave node /home/ec2-user/jenkins/workspace/job-1

```

### Variables

Variables are used to store the values (or) data. Here, we are having 2 types of variables.

1. Global Variable

- Here, we’re declaring the environment variable after the agent. 

- We have to use $variable in stages to call the variables

Q) Single Global Variabel Script

```
Pipeline {
    agant any 

    environment {
        name = "Naveen Silver"
    } 
    stages {
        stage("Stage-1") {
            steps {
                echo 'Hi, my name is $name'  // $ used to define variable
            }
        }
    }
}

```
Click on Build and click on logs to see the output.
<Image>

Q) Multiple Global Variable 

```
Pipeline {
    agant any 

    environment {
        name = "Naveen Silver"
        topic = "DevOps" 
        platform = 'Linkdin'
        Duration = 90

    } 
    stages {
        stage("Stage-1") {
            steps {
                echo 'Hi, my name is $name, I'm learning $topic through $platform.'
                echo 'and the Course duration is $duration days'
            }
        }
    }
}

```
Click on Build and click on logs to see the output.
<Image>

2. Local Variable

- Local variable override the Global variable.

- We’re declaring local variable inside the stages.

```
Pipeline {
    agant any 

    environment {
        name = "Naveen Silver"
    } 
    stages {
        stage("Global Variable") {
            steps {
                echo 'Hi, my name is $name'
            }
        }
        stage ("Local Variable"){
            environment {
                name = "Naveen Thurkapally"
            }
            steps{
                echo "Hi, i'm $name"
            }
        }
    }
}

```
Click on build and here we have 2 stages. First is global and second is local variable. Now, you can easily find out the difference between local and global.
<Image>

So, when we’re using local variable means, some specific/particular stage we need another value. On that case we’re using local.


Pre-defined variables:
----------------------

    echo “$BUILD_ID” -  To know build counts

    echo “$BUILD_URL” - To know build URL

```printenv``` command is used to return all Pre-defined Variables.

This is all about local and global variables.

## PARAMETERS PIPELINE 

Instead of manually selecting parameters, we can write the code in pipeline
- For the first time build, Automatically selecting the parameters based on our code. 
    - For the 1st build → code will executed

- After 1st build, Go to configure and check the parameters selected (or) not and do 

- For the second time build, click on build with parameters, we can see the output
    - For the 2nd build → parameters executed

- Here, Overall we have to build 2 times to see our output
- We have to take parameters block after the agent

Note: Whenever we're using Parameter we don't need to sue Environment Block.

### String Parameter Pipeline 

```
pipeline {
    agent any 

    parameters {
        string(name: "person", defaultValue:"Naveen", description: "my name is ")
    }
    stages {
        stage("String Parameters"){
            steps {
                sh 'echo "Hi, My name is $person" '
                // Another way  
                sh 'echo Hi, My Name is "${person}" '
            }
        }
    }
}
```
This is our code, click on save and build. Here, our code will get executed.
<Image>

After the first time build, Automatically selecting the parameters based on our code.
<Image>

Click on build with parameters, you will get above image and now click on build.
<Image>

This is all about string parameters

### Boolean Parameter Pipeline

```
pipeline {
    agent any

    parameters {
        booleanParam(name:"db", defaultValue: "true", description: "")
    }
    stages {
        stage ("Boolean Parameters"){
            steps{
                sh 'echo "Hi, This is Boolean Parameter" '
            }
        }
    }
}
```
This is our code, click on save and build. Here, our code will get executed
<Image>

After the first time build, Automatically selecting the parameters based on our code.
<image>

Click on build with parameters, you will get above image and now click on build

In the above code We written defaultValue is true. So, db checkbox is enabled. if we write false it is disabled.
<image>

###  Choice Parameter Pipeline

```
pipeline {
    agent any 

    parameters {
        choice(name: "file", choices:["Naveen", "Smiley","Cutie","Silver"], description: " My file is ")
    }
    stages {
        stage("Choice Parameters"){
            steps {
                sh 'echo "touch $file" '
            }
        }
    }
}
```
This is our code, click on save and build. Here, our code will get executed
<Image>

After the first time build, Automatically selecting the parameters based on our code.
<Image>

Here, we select the file names based on our requirements

Click on build with parameters, you will get above image and now click on build
<Image>

After build click on logs we can see the output

TASK 
====

Q) Write a Pipeline Script for getting multiple branch code from Github Using Variables and Parameters.

```
pipeline {
    agent any 

    parameters {
        choice(name: 'branch', choices:['master','main','azure','aws','gcp','mustafa','oracle'], description:'select the desired branch')
    }
    stages {
        stage("Choice Parameters"){
            steps {
                git branch:"${branch}" , url: 'https://github.com/devops0014/one.git'
            }
        }
    }
}
```

Click on Save and Build with Parameters.
<Image>

Select any Branch and Build it and Check the output in Jenkins Server Jobs.
<Image>

Here, If you select other branch next time. this branch files will be stored. previous branch files will be erased. 
<Image>

In this Case we use "Multi Branch Pipeline"


Pipeline Syntax / Pipeline Syntax Generater:
---------------------------------------------

Used to generate Pipeline syntax.

After giving the requirement steps. it will generate the syntax.


# WEBHOOKS (Pending)

<Jenkins-7 Video FLM>


## Post Build Actions / Functions Pipeline

A Jenkins Post-build action is a task executed after the build has been completed
- When you perform build, you won’t care about the build whether it is success(or) fail. Automatically, you want to build the particular stage 
- On that case we’re using post build actions

Here, we are having post conditions in jenkins

1. Success
2. Failure
3. Always
---
1. Success 

When the above stage build gets success means, then the post block will executed.

```
pipeline {
    agent any
    stages {
        stage ('Stage-1'){
            steps {
                echo ' Post Build Actions'
            }
        }
    }
    post {
        success {
            echo " The Above Stage-1 is Success "
        }
    }
}
```
Click on Save and Build
<image>

2. Failure

When the above stage build gets failed means, then the post block will executed

```
pipeline {
    agent any
    stages {
        stage ('Stage-1'){
            steps {
                eco 'Post Build Actions'   // h removed for stage failure
            }
        }
    }
    post {
        failure {
            echo " The Above Stage-1 is Failure "
        }
    }
}

```
Click on Save and Build
<image>

3. Always

When the above stage build either success (or) Failure. This post block don’t care it will always executed


```
pipeline {
    agent any
    stages {
        stage ('Stage-1'){
            steps {
                echo 'This is Stage-1'
            }
        }
        stage ('stage-2'){
            steps {
                eco 'This is Stage-2'
            }
        }
    }
    post {
        always {
            echo " The Above Stage-1 is Success always "
        }
    }
}
```
Click on Save and Build
<image>

Q) Write a Pipeline Syntax For Multiple Post Build Action Condition ?

```
pipeline {
    agent any 
    stages {
        stage ('stage-1') {
            steps {
                echo 'post build actions '
            }
        }
    }
    post {
        success {
            echo 'print stage-1 success'
        }
        failure {
            echo "print if stage-1 is failure"
        }
        always {
            echo "print always if stage-1 is fail or success"
        }
    }
}

```
Click on Save and Build
<image>

This is all about Post-Build Actions




### Custom WorkSpace - Pending

<Time Laps 25min>

### Parallel Stages

```
pipeline {
    agent any
    stages {
        stage ("Stage-1"){
            parallel {
                stage("stage-2"){
                    steps{
                        echo "stage-2 is parallel to stage-1"
                    }
                }
                stage("stage-3"){
                    steps{
                        echo "stage-3 is parallel to stage-1"
                    }
                }
            }
        }
       
    }
}
```
Click on Save and Build
<image>

Basically the Build stages will build one after another but here, we can see Build stages done parallelly. i.e, when the stage-1 is build then automatically stage-2 and stage-3 gets build at a time.

Q) What if any stage got failure ?

```
pipeline {
    agent any
    stages {
        stage ("Stage-1"){
            parallel {
                stage("stage-2"){
                    steps{
                        eco "stage-2 is parallel to stage-1" // failure
                    }
                }
                stage("stage-3"){
                    steps{
                        echo "stage-3 is parallel to stage-1"
                    }
                }
            }
        }
       
    }
}
```

Click on Save and Build
<image>

In Parallel Stages, If the any stage gets fail, it will go for next stage.

### Input Function Pipeline 

It takes the input from the user, based on the input it will performs the operations.

Here, we are taking the input from the user

- If User said OK means build will happen
- If User said NO means build will fail

 So, here we are having one condition. That condition we can called input function

- Here continuous integration performed. i/e, build +test

- But when it comes to deploy stage. It has to be asked the input from the user

Real-Time Scenario:

- Whenever you’re doing deployment, this input function we have to give to approval manager. So, manager check everything. If everything is correct he will click OK i.e., he will approve the deployment
 
- Here, how we’re giving the permissions means we’re using role based strategy and for all managers. we have to give full build perform permissions.

```
pipeline {
    agent any 
    stages{
        stage("Input Function"){
            steps{
                sh 'echo "This will Print acc to Users input" '
            }
            input{
                message " Are You sure ?"
                ok "Yes"
            }
        }
    }
}
```
Click on save and build you will get below image.
<image>

Here, if we click on yes means build will success, Click on abort means build aborted/stopped.


Once you click on yes,  you will get  below image.
<image>

This is all about input function

Q) For Multiple User Permissions 

```
pipeline {
    agent any
    stages{
        stage("stage-1"){
            input {
                message "Press Ok to Continue ?"
                submitters "user1, user2"         // Not Mandatory 
                parameters{
                    string(name:"username", defaultValue: "user", description:" User Permission" )
                }
            }
            steps {
                echo "${username} said ok to me, so that i can build"
            }
        }
    }
}
```
Click on save and build you will get below image.
<image>

Select the Particular user for permission and Proceed.

Note : This Job will success without "Submitter". which is used to Provide default users list.

Task ON PARAMETERS
-------------------

Q) Input Parameter Using IF-ELSE Conditions.

```
pipeline {
    agent any
    parameters{
        string(name: 'NAME', description: 'Please tell me your Name')
        choice(name: 'GENDER', choices: ['Male', 'Female'], description: 'Choose Gender')
    }
    stages{
        stage("Printing Name"){
            steps {
                script{
                    def name = "${params.NAME}"
                    def gender = "${params.GENDER}"
                    if(gender=="Male"){
                        echo "Mr. $name"
                    }else{
                        echo "Mrs. $name"
                    }     
                }
            }
        }
    }
}
```
Click on Save and Build with Parameters.
<Image> <Jenkins-8 Video>

# Master & Slave Connection Through SSH-KEYGEN
<image>

1. Launch 3 Instaces at a time using with key-pair

- Here Name the 3 instances like Master, slave-1, slave-2 for better understanding.

2. Connect Master server

a) Set up Jenkins 

- To See list of users ```cat /etc/passwd```

b) Set Password to Jenkins User

- To Set Password for users ```passwd <username>```

c) Full Root Permission to Jenkins User

- Go to ```visudo``` and Go to 100th line ``:100``

- Add ```jenkins ALL=(ALL)      NOPASSWD: ALL``` it in 101 linw and Save it ``:wq``.

d) Password Authentication 

- Go to ```vi /etc/ssh/sshd_config```

- Go to 63rd line ``63`` and Change it as ``PasswordAuthentication YES``

e) Restart SSHD

- To Restart sshd ``` systemctl restart sshd ```

3. Connect Slave-1 server

a) Add Jenkins user

- To Create ``useradd jenkins``

- To See list of users ```cat /etc/passwd```

b) Set Password to Jenkins User

- To Set Password for users ```passwd jenkins```

c) Full Root Permission to Jenkins User

- Go to ```visudo``` and Go to 100th line ``:100``

- Add ```jenkins ALL=(ALL)      NOPASSWD: ALL``` it in 101 linw and Save it ``:wq``.

d) Password Authentication 

- Go to ```vi /etc/ssh/sshd_config```

- Go to 63rd line ``63`` and Change it as ``PasswordAuthentication YES``

e) Restart SSHD

- To Restart sshd ``` systemctl restart sshd ```

4. Connect Slave-2 server

- Repeat the Slave-1 Configuration as it is.

NOTE : We are connecting through SSH connection. So, we don't need to install Dependencies i.e, Java

5. Establish Connection Between Master and Slave 

a) Go To Master and Go inside jenkins user `` su - jenkins``

- We can't go directly inside user. For that ``vi /etc/passwd`` go to last line using `G` and Change `false` to `bash` i.e, jenkins:/bin/bash

- Now Go inside Jenkins user `su - jenkins`

b) Generate SSH-key

- To Generate key `ssh-keygen` [Click on triple enter]

- Generated key saved in `/var/lib/jenkins/.ssh/id_rsa` (same like .pem file)

- Go and Check `ls -al` and open `cd .ssh`

c) Connecting to Slave 

- To Connect Slave Server `ssh-copy-id jenkins@<Slave_Public_IP>`

- If you give 'yes` and it will ask slave jenkins password 

d) Loggin Into Slave Server in Master

- Logging into slave server with `ssh jenkins@<Slave_Public_IP>`

- Now we are in Slave server from Master. Here we can see `[jenkins@ip-<slave_Private_Ip> ~]$ `

- Now, Perform some tasks here `$ touch files{1..5}`

- Connect Slave server and Go to jenkins user `su - jenkins` and check files.

- `exit` used to Exit from present user

Same way we can connect with Multiple slave servers using SSH

NOTE: Using SSH-Key we are connected to Slave MACHINE from MASTER MACHINE

Architecture
-------------

```          
           <<<<<<<<<<<< Slave-1
          /   ssh
Master   /<<<<<<<<<<<<< Slave-2
         \    ssh
           <<<<<<<<<<<< Slave-3
```

Here, we are Connected other slave servers with Master by generating ssh-key in Master.

Task :
------

Q) Establish a connection b/w Slave-1 to Other servers

- Connecting other servers with Slave-1.

- For that, We have to generate a ssh-keygen in slave-1

- Connect ssh-key with other servers

Q) How to Disconnect SSH-KEY Connection

- Go to `cd /var/lib/jenkins/.ssh/`

- Here, we can see authorised_keys, id_rsa, id_rsa_pub, known_hosts

- Remove files.


# Master & Slave Connection (Key-Pair)


Tasks On Pipeline Job
--------------------

Q) Maven Build Pipeline Script

```
pipeline {
    agent any
    environment {
        PATH = "$PATH:/opt/apache-maven-3.9.1/bin"
    }
    stages {
        stage('Get Code') {
            steps {
		git branch : 'main',
                 url : 'https://github.com/ashokitschool/maven-web-app.git'
            }
        }
        stage ('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}
```


Q) JENKINS PIPELINE (JENKINS + MAVEN + GIT HUB + SONAR + TOMCAT)

Create 3 Ec2 Instances 

	>> Jenkins with .pem file 

		>> Connect Instance and start the server 

		>> Connect the Jenkins Dashboard using 8080

	>> Tomcat Server

		>> Connect Instance and start the server 

		>> Connect the Tomcat Dashboard using 8080 (Change the port if you want)
		
	>> SonarQube Server

		>> Connect Instance and start the server 

		>> Connect the SonarQube Dashboard using 9000 

Note: Install 'SSH Agent Plugin' and Generate code using "Pipeline Syntax" 

    > Now Create a Job In Jenkins Dashboard 

    > Go To Pipeline and Click on "Pipeline Syntax"
		
	> Go to Snippet Generator

	> Steps > Simple step > Select "sshagent: SSH-Agent" Option

		>> sshagent : ec2-user (default)

			>> click on 'Add' and Add Credentials using SSH Username with Private Key (Jenkins VM .pem)

			>> ID : Tomcat-Server-Agent 

			>> Description : Tomcat-Server-Agent Credentials

			>> Username : ec2-user

			>> Private Key > .pem file > Add 

		>> sshagent : add created agent i.e ec2-user(Tomcat-Server-Agent)

		>> Click on Generate Script  (it will generate the script)

```
sshagent(['Tomcat-Server-Agent']) {
	//some block 
	sh 'scp -o StrictHostKeyChecking=no target/01-maven-web-app.war ec2-user@<Tomcat_Public_IP>:/home/ec2-user/apache-tomcat-9.0.63/webapps'
}

```		

Q) why we are using ssh-agent in pipeline script ?

Basically ssh is used for Communication between two machines 

here, ssh-agent is used to connect jenkins server to tomcat server and to copy the war file from jenkins server to tomcat server.


```
pipeline {
    agent any
    environment {
        PATH = "$PATH:/opt/apache-maven-3.9.1/bin"
    }
    stages {
        stage('Get Code') {
            steps {
                git 'https://github.com/ashokitschool/maven-web-app.git'
            }
        }
        stage ('Build') {
            steps{
                sh 'mvn clean package'
            }
        }
        stage ('SonarQube Analysis') {
	// def scannerHome=tool 'SonarScanner 4.0';
            steps {
                withSonarQubeEnv('Sonar-Server-7.8') {
	// if you have configured more than one global server connection, you can specify it's name 
		// sh "${scannerHome}/bin/sonar-scanner"
                    sh 'mvn sonar:sonar'
                }
            }
        }
        stage ('Code Deploy') {
            steps {
                sshagent(['Tomcat-Server-Agent']) { 
		// ssh agent - establish connection between 2 vm's
                    sh 'scp -o StrictHostKeyChecking=no target/01-maven-web-app.war ec2-user@<Tomcat_Public_IP>:/home/ec2-user/apache-tomcat-3.9.1/webapps'
                    // using ssh agent copying war file from Jenkins server to Tomcat Server
                }
            }
        }
    }
}

```
Now, Execute the Job 

Check Job Console output in Jenkins. we can find the job executed location.
	path: /var/lib/jenkins/workspace/<jenkins_job> (target folder available)

Check the output in Tomcat Server 

Successfully Application deployed in server


Task 
----

Q) Change the code in Git Hub and Execute the Job 

Go to GitHub ``` 'https://github.com/ashokitschool/maven-web-app.git' ```

Make some changes in Git Repo and Execute Job.

Go To SonarQube and Check the Bug Report

Go To Tomcat Server and Check the Deployement Output.

Q) How To Deploy Project to Multiple Environments Using Script Pipeline ?

We can Deploy our Project to Multiple environment. 

For Every Environment, we need to write one stage Script

For suppose you want deploy the Application to 'SIT' Environment.

First Create SSH-Agent For SIT server and Copy war file to SIT Server

```
 stage ('Code Deploy In SIT Server') {
            steps {
                sshagent(['Tomcat-SIT-Server-Agent']) { 

		sh 'scp -o StrictHostKeyChecking=no target/01-maven-web-app.war ec2-user@<SIT_Tomcat_Public_IP>:/home/ec2-user/apache-tomcat-3.9.1/webapps'
		}

```

Q) Write a script lines for getting code from GitHub Particular Branch 

```
steps {
	git branch: 'main', url: <Git-Repo-URL>
```

## Email Notifications In Jenkins :

We can configure Email notifications in Jenkins 

With this option we can send email notification to team members after job execution completed.

We need to configure SMTP properties to send emails.

Note : Install 'Email Extentions Plugin' 

> Go to Manage Jenkins > Configure System

> Go to 'Extended E-mail Notification'

> we will add company SMTP server Details 

    > SMTP Server : smtp.gmail.com

    > SMTP Port : 587

    > Add Credentials > Username : GMail and Password : Gmail Pwd (Used for Authentication Purpose) - Select SSL/TLS

Note: For Practice, we can use Gmail SMTP properties.

Once SMTP properties added then we can configure email notification as 'Post Build Action' in Jenkins Free-Style Job

In Pipeline Script we can configure the email notificationusing below script 

```
pipeline {
    agent any
    stages {
        stage('Hello') {
            steps {
				echo "Hello Babess.."
			}
		}
	}
	post {
		always {
			mail to : "silver@gmail.com",
			subject : "Test Mail"
			body : "Test"
		}
	}
}

```



# MULTI-BRANCH PIPELINE [PENDING]

<Jenkins-9 Video>


In Github, If we have Multiple branches and want to build multiple branches at a time.

Jenkins file is Mandatory in Each-Branch

 
A Multibranch job is a simply a Folder of Pipeline Jobs. For every branch you have, Jenkins will create a folder. So instead of creating a pipeline job for each of branches you have a git repo. You could use a multibranch job. this means that you'll have to create only one Job.






## Interview Questions : 

Q) How to stop Jenkins Server in Browser

Access below URL in Browser to stop Jenkins Server.

URL : http://Ec2-IP : 8080/exit 

> 166.56.16.1:8080/exit 

> Click 'Retry using post'

> Shutting Down Automaticaly  



