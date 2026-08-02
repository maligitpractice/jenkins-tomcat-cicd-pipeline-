# jenkins-tomcat-cicd-pipeline-
jenkins-tomcat-cicd-pipeline
# 🚀 CI/CD Pipeline: Deploying a Sample WAR Application from Jenkins to Apache Tomcat

![Jenkins](https://img.shields.io/badge/Jenkins-CI%2FCD-red)
![Tomcat](https://img.shields.io/badge/Apache-Tomcat-orange)
![Java](https://img.shields.io/badge/Java-21-blue)
![Ubuntu](https://img.shields.io/badge/Ubuntu-22.04-E95420)
![AWS](https://img.shields.io/badge/AWS-EC2-FF9900)

## 📌 Project Overview

This project demonstrates a simple Continuous Integration and Continuous Deployment (CI/CD) pipeline using **Jenkins** to deploy a Java web application (`sample.war`) to **Apache Tomcat** running on an AWS EC2 Ubuntu instance.

The objective is to automate application deployment using the **Deploy to Container Plugin** available in Jenkins.

---

# 📖 Project Objective

The primary objective of this project is to:

- Install Jenkins on Ubuntu EC2
- Install Apache Tomcat
- Configure Tomcat Manager
- Configure Jenkins
- Deploy a Sample WAR Application
- Automate deployment using Jenkins
- Verify deployment through Tomcat

---

# 🏗 Project Architecture

```
                GitHub / Local Repository
                          │
                          │
                          ▼
                    Jenkins Server
                          │
             Deploy to Container Plugin
                          │
                          ▼
                 Apache Tomcat Server
                          │
                     sample.war
                          │
                          ▼
                    Web Browser
```

---

# 🛠 Technology Stack

| Technology | Purpose |
|------------|---------|
| AWS EC2 | Hosting Server |
| Ubuntu Linux | Operating System |
| Java 21 | Runtime |
| Jenkins | CI/CD Tool |
| Apache Tomcat 9 | Application Server |
| Deploy to Container Plugin | Deployment |
| Sample WAR | Demo Application |

---

# 📂 Repository Structure

```
Jenkins-Tomcat-Deployment
│
├── README.md
├── screenshots
│     ├── ec2.png
│     ├── jenkins.png
│     ├── tomcat.png
│     ├── console-output.png
│     └── sample-app.png
│
├── commands
│     └── installation-commands.txt
│
├── configuration
│     ├── server.xml
│     ├── tomcat-users.xml
│     └── context.xml
│
├── sample
│     └── sample.war
│
└── documentation
      └── ProjectDocumentation.docx
```

---

# 🚀 Step 1 - Launch AWS EC2 Instance

Create an Ubuntu EC2 instance with the following specifications:

- Ubuntu Linux
- Instance Type: m7i-flex.large
- 8 GB RAM
- 30 GB Storage

Connect using SSH or PuTTY.

---

# 🚀 Step 2 - Update Server

```bash
sudo su -
apt-get update -y
sudo apt update
```

---

# 🚀 Step 3 - Install Java

```bash
sudo apt install fontconfig openjdk-21-jre
java -version
```

Verify Java installation.

---

# 🚀 Step 4 - Install Jenkins

Follow the official Jenkins installation guide:

https://www.jenkins.io/doc/book/installing/linux/

Example commands:

```bash
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
```

```bash
sudo apt update
sudo apt install jenkins
```

Start Jenkins and access:

```
http://<EC2-Public-IP>:8080
```

Retrieve the initial admin password:

```bash
cat /var/lib/jenkins/secrets/initialAdminPassword
```

Complete the Jenkins setup wizard by installing the suggested plugins.

---

# 🚀 Step 5 - Install Apache Tomcat

Download Apache Tomcat 9.

```bash
wget https://downloads.apache.org/tomcat/tomcat-9/v9.0.120/bin/apache-tomcat-9.0.120.tar.gz
```

Extract the archive.

```bash
tar -xvzf apache-tomcat-9.0.120.tar.gz
```

---

# 🚀 Step 6 - Configure Tomcat

Edit

```
conf/server.xml
```

Change the default connector port from

```
8080
```

to

```
8081
```

Start Tomcat

```bash
cd bin
./startup.sh
```

Verify

```
http://<EC2-IP>:8081
```

---

# 🚀 Step 7 - Install Jenkins Plugin

Navigate to:

```
Manage Jenkins
```

↓

```
Plugins
```

↓

```
Available Plugins
```

Install

```
Deploy to Container Plugin
```

---

# 🚀 Step 8 - Create Jenkins Job

Create a new **Freestyle Project**.

Example:

```
autodeplyment
```

Add Build Steps as required.

---

# 🚀 Step 9 - Download Sample WAR

Navigate to the Jenkins workspace.

Example:

```bash
cd /var/lib/jenkins/workspace/autodeplyment
```

Download sample application.

```bash
wget https://tomcat.apache.org/tomcat-6.0-doc/appdev/sample/sample.war
```

---

# 🚀 Step 10 - Configure Tomcat Users

Edit

```
conf/tomcat-users.xml
```

Add users with the required manager roles.

Restart Tomcat after saving the changes.

---

# 🚀 Step 11 - Configure Jenkins Credentials

Navigate to

```
Manage Jenkins

↓

Credentials

↓

Global Credentials
```

Add the Tomcat deployment credentials.

---

# 🚀 Step 12 - Configure Deployment

Open the Jenkins project.

Select

```
Post Build Actions

↓

Deploy WAR/EAR to Container
```

Configure:

- WAR File
- Tomcat URL
- Credentials

Save the configuration.

---

# 🚀 Step 13 - Build Project

Click

```
Build Now
```

Monitor the deployment through:

```
Console Output
```

---

# 🚀 Step 14 - Verify Deployment

Open

```
http://<EC2-IP>:8081/sample/
```

If successful, the sample application page will be displayed.

---

# 📷 Screenshots

Include screenshots for:

- AWS EC2 Instance
- Java Installation
- Jenkins Dashboard
- Jenkins Plugins
- Jenkins Freestyle Project
- Build Configuration
- Console Output
- Apache Tomcat Home
- Tomcat Manager
- Sample Application

---

# 📌 Project Outcome

Successfully implemented a CI/CD pipeline that automates the deployment of a Java web application from Jenkins to Apache Tomcat using the Deploy to Container Plugin.

---

# 🔍 Troubleshooting

| Issue | Solution |
|--------|----------|
| Jenkins not accessible | Verify port 8080 in the Security Group |
| Tomcat not accessible | Verify port 8081 |
| Deployment failed | Check Jenkins Console Output |
| Authentication failed | Verify Tomcat Manager credentials |
| WAR not deployed | Verify Post Build configuration |

---

# 🔮 Future Enhancements

- Convert Freestyle Job to Jenkins Pipeline
- Store source code in GitHub
- Build using Maven
- Integrate SonarQube for code quality
- Store artifacts in Nexus Repository
- Build Docker images
- Deploy using Kubernetes
- Provision infrastructure using Terraform
- Automate configuration using Ansible
- Add Prometheus and Grafana monitoring
- Implement Slack or Email notifications

---

# 👨‍💻 Author

**Pakkirmalimar**

Senior DevOps Engineer

**Skills**

- AWS
- Jenkins
- Apache Tomcat
- Linux
- Docker
- Kubernetes
- Terraform
- Ansible
- Git
- CI/CD

---

## ⭐ If you found this project useful, consider giving it a Star.
