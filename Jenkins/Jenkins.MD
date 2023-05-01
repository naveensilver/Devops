## JENKINS

Jenkins is used for Continuous Integration and Continuous Delivery/Deployment (CI/CD).

### CI - Continuous Integration :

It is the combination of Continuous Build and Continuous Test.
  
C.I = C.B + C.T

Build and Test - These Two activities performing in a single task.

**BEFORE C.I :**

<image>
  
Multiple developers write the code, and the code is stored in Git Hub Repo.
  
After, we get the source code from git hub and Build the source code in Maven server and Generate Jar/War file.
  
These Jar/War Files tested in another server using Selinium/Junit.
  
If we get any bugs in source code, we can send it back to the developers and the developers fix the bugs/errors and again stored in github.

Note : Each activity performing in different server.
  
  - Manual work is high.
  - Build & Test in different servers
  - For Build = Maven/Ant/Gradle
  - For Test = Selenium/JUnit
  
**AFTER C.I :**
  
<iMAGE>

Here, Developers Write the code and store in GitHub Repo.
  
The source code repo is sendeing to CI server.
  
In CI server, The Build and Test will happen automatically.
  
CI Server = Automatic Build + Automatic Test 
  
* CI Server :

Here, The Build, Test and Deploy all the activities are performed in a single CI server.

  <Image>
    
If the code fails in CI server, we can send back to developers and developers fix the bugs.(Repeat)
    
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
    
<iMAGE>
      
      
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
  
<Image>

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
  
  Jenkins is first choice for Continuous Integration and It consists of Plugins 
  
  * Plugin is nothing but a small software, that we used to add some extra features to our jenkins dashboard.
  
  Jenkins Automates the entire SDLC 
  
  #### IMAGE ###
  
  By using single tool, we can intigrate and automate entire software development.
  
  Jenkins was originally developed by Sun Micro-System in 2004 and Named as HUDSON. Hudson was paid software.
  
  After Oracle bought from Sun Micro-System and Renamed as Jenkins and Given for free.
  
  It can run on any playforms without issues.
  
  Whenever developers write the code, we can integrate the code to all developers.
  
  At any point of time, we can Build, Test and Deliver/Deploy application to client. This is Called "CI/CD"
  
  DEV =========> Git ===========> Jenkins =========> Client.
  
  **Advantages :**
  
  Jenkisn follows Master-Slave Architecture.
  
  You can write own plugin, can use community plugins also.
  
  Can easily understand the process of what is going on.
  
  **Jenkins Alternatives :**
  
  BamBOO, Travious CI, Circle CI, Git Lab, Buddy, Teamcity, Sema4, AWS code Pipeline.
  
  
  ### MASTER-SLAVE ARCHITECTURE / MASTER ROLES :
  
  Master assign a jobs to the slaves. that slaves works on assigned Job/Work.
  
  If the slaves are not available, master itself done the job.
  
  By using lable, we can specify/assogn the job to the nodes/Slaves.
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
