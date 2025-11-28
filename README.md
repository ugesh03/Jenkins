# Jenkins
🚀 Project Overview

This guide walks you through:
Setting up an AWS EC2 instance
Installing necessary packages (JDK 21, Git, Maven, Wget)
Installing and configuring Jenkins
Integrating Maven with Jenkins
Creating and running a Maven project in Jenkins
Troubleshooting common issues

This setup is ideal for CI/CD pipeline beginners, DevOps learners, or anyone wanting to automate Java builds using Jenkins.

#🖥️ 1. AWS EC2 Setup
1.1 Launch an EC2 Instance
Use the following recommended configuration:
Setting	Value
Operating System	Red Hat Enterprise Linux 9
vCPUs	2
Memory	4 GB RAM
Storage	50 GB (GPSSD)
Required Ports	22 (SSH), 80 (HTTP), 8080 (Jenkins)

⚠️ Note: Port 8080 is required to access Jenkins.


#🔗 2. Connect to the Instance
Connect to the EC2 server using SSH (via PuTTY or terminal).


#📦 3. Install Required Software
Run the following commands after connecting to the instance:
  sudo yum update -y
  sudo yum upgrade -y
Install Java 21
  sudo yum install java-21-openjdk java-21-openjdk-devel -y
Install Git
  sudo yum install git -y
Install Maven
  sudo yum install maven -y
Install wget
  sudo yum install wget -y


#⚙️ 4. Install Jenkins
4.1 Add Jenkins Repository & Import GPG Key
sudo yum upgrade -y
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
4.2 Install Jenkins
sudo yum install jenkins -y
4.3 Enable & Start Jenkins
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins


#🌐 5. Access Jenkins Web Interface
Open your browser and visit:
http://<EC2-Public-IP>:8080
Retrieve the initial admin password:
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
Complete Jenkins setup and create your admin user.


#🔌 6. Install Essential Jenkins Plugins
It’s recommended to install:
Git Plugin
Pipeline Plugin
Blue Ocean
Maven Integration Plugin
Stage View Plugin


#🔧 7. Configure Maven in Jenkins
Go to Manage Jenkins → Global Tool Configuration
Under Maven, click Add Maven
Provide:
Name: Maven-3.6.3 (or your choice)
Installation directory: /usr/share/maven (if using system Maven)
Verify Maven install:
mvn -v


#🛠️ 8. Build a Maven Project in Jenkins
8.1 Prepare Git Repository
Ensure your Git repo contains a valid pom.xml.
8.2 Create Jenkins Job
Click New Item
Select Maven Project
Configure:
Source Code Management:Git repository URL
Credentials if required
Build:
Root POM: pom.xml
Goals: clean install
Post-build Actions (Optional):
Archive artifacts (*.jar, *.war)
Start the Build

Click Build Now and monitor the console output.

🧩 Troubleshooting
Issue	Solution
JDK version mismatch	Update Jenkins JDK configuration
Maven path not detected	Set correct Maven home in Global Tool Configuration
pom.xml not found	Provide correct relative path

Documention : 

[Jenkins Setup with Maven.docx](https://github.com/user-attachments/files/23819514/Jenkins.Setup.with.Maven.docx)


