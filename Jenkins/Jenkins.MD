### JENKINS

Jenkins is used for Continous Integration and Continous Delivery/Deployment (CI/CD).

* **Continuos Integration :** 

It is the combination of Continous Build and Continous Test.
  
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
    
    


