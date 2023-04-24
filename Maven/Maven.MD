# MAVEN 

Maven, Gradle, Ant --- Build tools developed by Apache Group.

In DevOps life cycle, we use Maven as a Build Tool 

### Maven

Maven is Popular and Open-Source Build Tool.

Maven is Automation of Project Management Tool and it is developed by Apache foundation.

Maven is based on POM.XML file.

*	POM – Project Object Model 

*	XML – Extensible Markup Language 

*	POM.XML is consists

    * Meta-data – Data about the data 
    * Dependencies – Like java, python.
    *	Kind of Output – Output 
    *	Kind of Project – Projects 
    *	Description 
   
Maven is Build Tool and Manage Dependencies (Used to add the dependencies to our app)

Maven is used to Build, Publish and Deploy several projects at a time for better project management.

Maven can build any no. of projects. Once we build the code, depend up on the code we get JAR/WAR/EAR files.

*	.jar – java archive file – If the code is in Java, Spring Boot.

*	.war – web archive file – Html, CSS, JS.

*	.ear – enterprise archive file – J2EE (Java Enterprise Edition)

Maven is written in Java and It was initially released on 13 July 2004.

Maven is used mostly for Java-Based Projects. (90%)

Maven helps in getting the right jar files for each project. For each project, it will separate packages for the different versions.

Maven can create initial Project folder structure.

Maven can download required Project dependencies. Visit mvnrepository.com

*	Dependencies – Refers to the java libraries that are needed for the project.

*	Repositories – Refers to the directories of packaged jar files. (Local, Central, Remote)

*	Build Tools: 
    *	Maven: Java, C#, Ruby, Scala.
    *	Gradle / Ant: Java 
    *	Nant: .Net  
    *	Py-Builder: Python
     
### Build Tool

Build tool is used to Setup everything. Which is required to run your java code. This can be applied to your entire java project.

Build tool generates the code, compile the code and packaging the code to a jar file.

POM refers the XML file that have all info regarding project and configuration details.

MAIN configuration file is in POM.XML

POM.XML file has description of project details regarding version and config management.

XML file is in the Project Home Directory.

*Note – One project consists of one workspace, each workspace consists of one POM.XML file.

### Java Project Structure

* Source code – Developers write the code

* Test the code – Testing the source code 

*	Project structure – We can check project files and folders (Asserts, Directories, Resources)

*	Dependencies/Libraries – Adding dependencies for our project 

*	Configuration – we need to configure 

*	Run task 

*	Reporting – if we get any error, we will report.

### Advantages Of Maven / Problem Without Maven 

* Adding set of jars in each project - Before maven we need to add jar/war files individually but after maven, once we build the code automatically generates war/jar files 

* Creating the right project structure - Before maven, we must create the right project structure. But maven will automatically create files & different versions for each project.

* Building and deploying the project 

### Q) What We Can Do Using Maven ?

- We can create initial project folder structure using Maven.

- We can download project dependencies using Maven.

- We can compile the source code into byte code using Maven.

- We can package Java project as jar/war file using Maven 

## MAVEN ARCHITECTURE :

![image](https://user-images.githubusercontent.com/120022254/233929742-55423375-09c9-4099-99e8-e0b46dd98ab0.png)

### Components 

* POM.XML 
   * Project Description 
   * Dependencies/Libraries 
   * Plugins (Task/Goals)
   * Project data 
   * Project Output 
   
* REPOSITORIES
   * Local Repo 
   * Central Repo  
   * Remote Repo 

### POM.XML 

Maven is based on Project Object Model (POM.xml)

When we create a maven project then POM.xml file is created automatically.

POM.xml file acts as input file for Maven.

POM.xml file is A Heart of Maven and it is Mandatory to work with Maven.

POM file is written by developers and it is placed along with the source code.

POM file contains all the information about the project and info about dependencies and plugins and location of remote repo path etc.

Note – Required dependencies are added in “POM.xml” file then maven will download them.

## How Maven Works :

Whenever we run any maven command. Ex: mvn compile, mvn test, mvn package

Maven will search for the information in this POM file and download the dependencies and plugins accordingly.

POM file is very important and mandatory for maven. Maven was downloading all the dependencies by getting the info from the POM file.

But, from where it is downloading dependencies and plugins.?

-	From repositories

### REPOSITORIES

Maven is having 3 Repositories.

1. Local Repo(.M2): 

* Local repo is nothing but on the same server where you are running maven server. So that is like a local cache.

* Whenever you give maven command, it will search the dependencies and plugins in the local repo.

* If they are not available in the local. Then it will go to central repo 

2. Central Repo: 

* It is the repo managed by the maven community. This will have all the widely used plugins, dependencies/libraries & jar files etc.

* So, Maven will search the central repo over internet and download the dependencies and plugins and placed them into local repo.

* Next time, if it’s need same dependencies and plugins. It will use them from local repo.

* It will not download again from the central repo. (No need for internet 2nd time)

* The workflow becomes faster.

* If it doesn’t find the dependencies and plugins in local & central repo. Then maven will go to remote repository.

3. Remote Repo: 

* It is a repository which is developed by the developers and it is the developers own custom created repository. It contains all the required libraries & jars for the project.

* Maven will download the required libraries from remote repo.

* This remote repo location will be documented in the POM.XML file.

Note: Every software company will maintain their own remote repository. Ex: JFrog

This is how maven will work through POM. So, the POM.xml is very important file.  
 
## Steps To Setup Maven :


## Maven Build Life Cycle :

Build life cycle consist of sequence of build phases & each build phase consist sequence of goals.

Each goal is responsible for particular task. Goal is nothing but a task/command

When a phase is run, all the goals related to that phase and it’s Plugins are also compiled.

1)	Generate Resources – Install Resources and Dependencies
2)	Compile Code – $ mvn compile 
3)	Unit Test – $ mvn test 
4)	Package (Build) – $ mvn package
5)	Install (Into local repo or Artifactory) – $ mvn install 
6) Deploy – By integrate with Jenkins, we can deploy to servers
7) Clean (To delete all the run time files) – $mvn clean 


## MAVEN DIRECTORY STRUCTURE :

![image](https://user-images.githubusercontent.com/120022254/233935817-83392eb3-4bd0-4d7d-b0ec-07975730419b.png)
![image](https://user-images.githubusercontent.com/120022254/233935885-783a6d74-5774-4920-880e-0522ac8a9376.png)



