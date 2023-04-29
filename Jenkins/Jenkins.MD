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
  
  we need server = EC2-Instance
  
  Database for storing data - RDS
  
  For Networking - VPC
  
  For Storing - S3
  
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
  
  
      
