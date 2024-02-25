Session-24
=======

what is sonar 
what is code coverage & code review 
how to setup sonar server
sonar admin login 
sonar rules 
sonar quality profiles and create customise profile 
make custom profile as default 
using Quality profile for particular projects 
sonar quality gate and create customise gate conditions
sonar integration with maven project 
Sonar Token Generation 
Sonar server integration with Jenkins Using Pipeline Job
=======================================

Sonar Qube 
++++++++

Sonar Qube is Continuous Code Quality checking Tool.
Sonar Qube is used to Review the code.

What is Code Coverage & Code Review
=========================

Code Coverage : How many lines of source code is tested by unit test cases.

	>> Note : Industry standard code coverage is 80% 

Code Review : Checking Coding Converntions.

Why Sonar Qube 
++++++++++++

Sonar Qube is open source software quality management tool.

It will continuosly analyse and measures quality of source code.

It will generate, code review report in html format / pdf format

It is a web based tool and it supports 20+ Programming languages

It will supports Multi OS Platforms (Linux, Windows..)

It will support multiple databases (MySQL, Oracle, SQL Server, PostGres SQL...)

It supports multiple browsers.

Sonar Qube will identify below category of issues in project source code.
	
	>> Duplicate Code
	>> Coding Standards
	>> Unit Tests 
	>> Code Coverage 
	>> Complex code 
	>> Commented code 
	>> Potential Bugs

Initially SonarQube war developed only for Java Projects.

But, Nowadays Sonarqube is Supporting for 20+ Languages.

Open source: Java, Java Script, C#, Web Technologis (HTML, JSP), XML, Python, Groovy, Puppet etc..

Commercial ; ABAP, C, C++, COBOL, PL/SQL, Visual Basic, VB.net, Swift etc.


Environment Setup 
+++++++++++++

Java is the Pre-Requisite software to run SonarQube

Sonar 7.8v   -------------> Java 1.8v is Required.
Sonar 7.8 - 8v -----------> Java 11v is Required.

Note: We can check this compatability in official sonar website.

Hardware Requirements
================

Min Ram - 2GB Required to run SonarQube. So, we go for t2.medium

t2.micro ------ 1 GB Ram 
t2.medium --- 4 GB Ram 


Sonar Qube Architecture
=================

1) SonarQube Scanner
	>> It will take source code as input and it will generate report.
2) SonarQube Server
	>> SonarQube server contains 3 components 
		1. Compute Engine
			>> Vulnerabilities 
			>> Bugs 
			>> Code Smells 
		2. Database
		3. Webserver
		4. Search Engine
	
Note: Compute Engine will store report into H2 DB (We can configure external DB also)

	- WebServer (It will display report in webserver)

Note: Developers will see sonar report and will fix the issue

	- Sonar Engine (it will give search results)


>> Session - 25 
===========

Steps To setup SonarQube in Linux
++++++++++++++++++++++++

Create Ec2 Instance with 4GB Ram (t2.micro)

Connect with Ec2 Instance 

Check Space : $ free -h 

$ sudo su 
$ cd /opt 
$ sudo yum install java-1.8.0-openjdk
$ java - version 
$ yum install wget unzip -y 
$ wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-7.8.zip

$ unzip sonarqube-7.8.zip

Note: SonarQube server will not run with root user

>> Create new user 
$ useradd sonarqube
$ visudo 

>> Configure sudo user without passwd
	sonar ALL=(ALL) NOPASSWD: ALL 
>> Change ownership and Permissions for sonar folder
		$ sudo chown -R sonarqube:sonarqube /opt/sonarqube-7.8
		$ sudo chmod -R 777 /opt/sonarqube-7.8

$ sudo su - sonarqube (Switching to sonarqube user)

Go to bin directory then do to linux directory and run sonar server

$ cd /opt/sonarqube-7.8/bin/linux-x86-64/

$ sh sonar.sh start  or ./sonar.sh

Check sonar Server 
$ sh sonar.sh status 
 
Note : Sonar server runs on 9000 port number by default 
	>> Enable port number in Ec2 Vm-Security Group

Access Sonar Server in Browser
	URL : http:// VM-IP:9000/

Default credentials of sonar User is admin & Password is admin 
After login, we can go to security and we can enable force Authentication.
	>> Go to Administration > Configuration > General Settings > Security > Force user authentication : ENABLE 

++++++++++++++++++++++++++++++

Note : If the sonar is not started, then go to log file and see 
	$ sudo rm -rf /opt/sonarqube-7.8/temp/
	and start the server
=======================================
 Change SonarQube Port
+++++++++++++++++

Go to SonarQube Directory 

$ cd /opt
$ cd sonarqube-7.8
$ cd conf/
$ vi sonar.properties 
	/9000 or 113 line

===================================

How to integrate Sonar Server with Java Maven App
+++++++++++++++++++++++++++++++++++

Go to "Pom.xml" file and Configure sonar properties under <properties/> tag.

<properties>
	<sonar.host.url>sonar-server-url</sonar.host.url>  #add sonar url
	<sonar.login>username</sonar.login> 	#username : admin 
	<sonar.password>pwd</sonar.password> 	#pwd : admin
</properties>

Go to pom.xml file location and Execute below goals.

	$ mvn clean package  #To Build the Project Code 

	$ mvn sonar:sonar	#To Analysis/Perform the code review 

After Build Success, Go to Sonar Dashboard and Varify that "1 Project Analysed" and also we can see "Bugs" and 'other' options.

==============================================================================================
 
Note: Instead of Username and Password, we can configure Sonar 'Token' in pom.xml

Working with Sonar Token (Recommended)
+++++++++++++++++++++++++++++

Go to Sonar > Click on profle > My Account > Security > Generate token 
	>> Note: In this path we can change admin password also 

Copy the token and Go to "Pom.xml" file and Configure Sonar properties under <properties/> tag.

<properties>
	<sonar.host.url>sonar-server-url</sonar.host.url>
	<sonar.login>token</sonar.login>
</properties>

Go to pom.xml file location and Execute below goals.

	$ mvn clean package  #To Build the Project Code 
	$ mvn sonar:sonar	#To Analysis/Perform the code review 

================================================

Quality Profile ?
+++++++++++

Quality profile is nothing but a set of rules given by sonar for every languages to perform code review.

so, whenever you do the code review by using sonar that language specific quality profile will be executed according to profile quality code rules.

For each language sonar qube provided one quality profile with set of rules.

The Default Quality Profile is Sonar way.
	>> For Java-381 Default Rules available 
	>> For Go - 29 Default rules available	

If the code is not matching those rules, then issues will be reported by the sonar.

If you don't want to follow all those rules of sonar then you need to create your own quality profile and customise(Activate) the rules.

You need to make your profile as a default profile. then sonarqube will review the code by using custom profile rules that you have configured.

Note : we can make our quality profile as default one then it will applicable for all the projects which gets reviewed under this sonar server
==========================

Q) How to create custom quality profile in the sonar ?

We can create our own quality profile based on project requirement.

To create one Quality Profile 
	> Name : SBI_Project 
	> Language : Java 
	> Parent : None 

Note : If we have any common ruleset for all projects then we can create one quality profile and we can use that as parent quality profile for other project.

>> we can configure Quality Profile to specific project 
	- Go to projects > click on Project name  
	- Go to administration
	- Click on Quality profile
	- Select Required Profile for Java language.
================================

Q) How to customise the sonar rules for the java project ?
 
=========================================

Quality Gate
+++++++++

Quality gate is nothing but final report. (pass/fail)

Quality gate is a set metrics/measurement to decide the project code is passed in the code review or failed in the code review. 

Every project quality gate should be passed.

In Sonar, The Default Quality gate is Sonar way 

If Required, We can create our own Quality gate and customise the conditions.

Note: If project quality gate is failed then we should not accept that code for deployment.

===========================================

Q) How to create Quality gate in sonar ?

Q) How to customise the Sonar Quality gate Conditions.

==================================================

Why we customise the Quality Profile and Quality Gate ?
++++++++++++++++++++++++++++++++++++

Based on the Project requirement, we will customise the Quality Profile & Quality Gate Rules.

If the developers want to follow all the rules of the sonar. Then you no need to customise the rules.

In some project, the developers follow all the default Profile rules. 
	>> If they go with default profile rules that means more quality will be their.

In some projects, the developers asks to create a new profile and customise the rules. 
	>> If the developers go with the custom profile rules that means quality of code will be less 

=============================================================================================
 How the sonar issues solved & who will solve ?
==============================

If the Project is having sonar issues then developement team is responsible to fix those issues.

As a DevOps enginees, we will perform code review and we will send code review report to Development team (we will send sonar server URL to Development team)

============================================================================================
Session - 26
++++++++++++++++++++
Jenkins integration with Sonar 
++++++++++++++++++++

Pre-Requisites
==========
1) SonarQube server 
	a) Generate a token (To establish connection with Jenkins)

2) Jenkins Server 
	a) Install Apache Maven 
	b) Install SonarQube Scanner 
	c) Configure SonarQube Server with Token
	d) Add SonarQube Scanner 
	e) Jenkins Pipeline Job 

===================================

Procedure 
=======

>> Create 2 Instances (Jenkins Server, SonarQube Server)

1) Connect to SonarQube Server and Start SonarQube Server 
	>> Access the SonarQube Server in Browser (Public_IP:9000) 
		a) Generate Token 

2) Connect to Jenkins Server and and Start Jenkins server 

a) Install Apache-Maven in jenkins server VM 
		$ sudo su 
		$ cd /opt 
		$ wget https://dlcdn.apache.org/maven/maven-3/3.9.1/binaries/apache-maven-3.9.1-bin.tar.gz
		$ tar -zxvf apache-maven-3.9.1-bin.tar.gz
		$ cd apache-maven-3.9.1-bin.tar.gz
		

	>> Access the Jenkins Server in Browser (Public_IP:8080)

b) In-order to integrate Jenkins with sonar. we need to install "SonarQube Scanner for Jenkins" Plugin in jenkins 

	>> Go to Manage Jenkins > Available > SonarQube Scanner > Install 

c) Once SonarQube Scanner is installed, we need to configure Sonar server credentials on Jenkins.

	>> Go to Manage Jenkins > Configure system > SonarQube Servers >> Add SonarQube 
		>> Name : Sonar-Server-7.8
		>> Server URL : http://52.66.257.11:9000/ (Give your sonar server url)
		>> Add SonarQube Server Generated Token 
			>> Note : Token should add as secret text
		>> Apply & Save


d) Add SonarQube Scanner
	>> Go to Manage Jenkins > Global Tools Configuration > SonarQube Scanner
		- Name : Sonar-Scanner-4.7
		- Select Sonar Version (SonarQube Scanner-4.7)
		- Save 

e) Create Jenkins Pipeline Job 
	>> Click on New Item > Enter Job Name and Select Pipeline 
	>> Go to Pipeline Section and Enter Below Script (Groovy Sandbox)

---------------------------------------
Build Pipeline +SonarQube Server
-----------------------------------------

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
    }
}


>> Build the Job and check the console o/p 

>> Go and Check the Project in SonarQube Server

=============================================

Note: If you select Free-Style Project job use below step 
Select jenkins job > Configure > Under "post-build actions" > SonarQube analysis with Maven

=================================================
