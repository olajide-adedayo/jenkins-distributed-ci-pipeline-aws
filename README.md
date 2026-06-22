# 🚀 Jenkins-Based Continuous Integration (CI) Pipeline with Distributed Build Architecture on AWS

![Jenkins](https://img.shields.io/badge/Jenkins-CI/CD-red)
![AWS](https://img.shields.io/badge/AWS-Cloud-orange)
![Maven](https://img.shields.io/badge/Maven-Build-blue)
![GitHub](https://img.shields.io/badge/GitHub-VersionControl-black)
![DevOps](https://img.shields.io/badge/DevOps-Automation-green)

## 📌 Project Overview

This project demonstrates the implementation of a *Continuous Integration (CI) pipeline using Jenkins on AWS*, designed to automate source code integration, build execution, testing, and artifact generation for a Java-based web application.

The pipeline was initially implemented as a traditional Jenkins build system and later extended into a *distributed build architecture using a dedicated Jenkins Agent deployed on AWS EC2*.

This setup simulates a real-world DevOps CI environment where build workloads are separated between a Jenkins Controller and multiple build Agents for improved scalability and performance.


## 🎯 Business Objective

To design and implement an automated Continuous Integration (CI) pipeline that:

- Integrates source code from GitHub
- Automates Maven-based build lifecycle
- Compiles and tests application code
- Generates deployable WAR artifacts
- Implements distributed build execution using Jenkins Agent architecture
- Demonstrates scalable, production-like CI/CD workflow on AWS infrastructure


## 🛠️ Technologies Used

- Jenkins (CI/CD Automation Server)
- AWS EC2 (Cloud Infrastructure)
- Ubuntu Linux (Operating System)
- Git (Version Control System)
- GitHub (Source Code Repository)
- Maven (Build Automation Tool)
- Java OpenJDK 21 (Application Runtime)
- SSH (Secure Remote Communication)
- Maven Central Repository (Dependency Management)


## ☁️ AWS Infrastructure

### Jenkins Controller Server
- AWS EC2 Instance
- Ubuntu Linux
- Jenkins Installed and Configured
- Git & Maven Integration Enabled

### Jenkins Agent Server (Maven Builder)
- AWS EC2 Instance
- Ubuntu Linux
- OpenJDK 21 Installed
- Configured as Jenkins Build Agent
- Connected via SSH to Jenkins Controller
- Assigned Label: MAVEN-BUILDER


## ⚙️ Jenkins Configuration

### Installed Tools in Jenkins

- JDK: OpenJDK 21 configured in Global Tool Configuration  
- Maven: Maven 3.9.x configured for build automation  
- Git: Installed on Jenkins Controller for source code retrieval  
- SSH Client: Used internally by Jenkins for agent connectivity via SSH  

---

### Jenkins Node Configuration (Agent Setup)

- Node Name: MAVEN-BUILDER  
- Remote Root Directory: /opt/jenkins  
- Launch Method: SSH (Launch agents via SSH)  
- Credentials: SSH Username with Private Key (ubuntu user)  
- Host Key Verification Strategy: Non-verifying strategy  
- Label: MAVEN-BUILDER  
- Number of Executors: 1 (controlled resource usage for build stability)  

---

### AWS EC2 Infrastructure Supporting Jenkins

#### Jenkins Controller Server
- Ubuntu Linux (EC2 Instance)  
- Jenkins Installed and Running  
- Git Installed  
- Java (OpenJDK 21) Installed  

#### Jenkins Build Agent (Maven Agent)
- Ubuntu Linux (EC2 Instance)  
- OpenJDK 21 Installed  
- Remote workspace configured at /opt/jenkins  
- Connected to Jenkins Controller via SSH  

---

### Job Configuration

- Source Code Management: GitHub integration  
- Repository URL: https://github.com/HKHcoder/vprofile-project.git  
- Build Trigger: Manual execution  
- Build Tool: Maven  
- Build Goal: mvn install  
- Execution Mode: Restricted to MAVEN-BUILDER node (Distributed Build Architecture)  
- Artifact Generated: WAR file (vprofile-v2.war)  

---

### Build Output

- Artifact Location: target/vprofile-v2.war  
- Build Status: SUCCESS  
- Artifact Archiving: Enabled in Jenkins


## 🔄 Continuous Integration (CI) Pipeline Workflow

The CI pipeline was implemented using Jenkins to automate the full build lifecycle of a Java web application hosted on GitHub.

---

### Pipeline Flow

1. Developer commits and pushes code to GitHub repository  
2. Jenkins job is triggered manually (configured for CI execution)  
3. Jenkins pulls the latest source code from the GitHub repository  
4. Maven resolves all project dependencies from Maven Central Repository  
5. Source code is compiled into bytecode  
6. Automated unit tests are executed using Maven Surefire plugin  
7. Application is packaged into a WAR file (web application artifact)  
8. Jenkins archives the generated artifact for future use  
9. Build is executed on a dedicated Jenkins Agent (MAVEN-BUILDER node) instead of the controller  
10. Build status is reported back to the Jenkins dashboard  

---

### Maven Build Lifecycle Executed

The following Maven phases were executed during the pipeline:

```text
clean → validate → compile → test → package → install

Maven Command Used

mvn clean install

Output Generated

. Artifact : vprofile-v2.war
. Location : target/vprofile-v2.war
. Build Status : SUCCESS
. Artifact Archiving : Enabled via Jenkins post-build actions

Key Note

This CI pipeline demonstrates a distributed build execution model, where Jenkins offload build processing to a dedicated agent (MAVEN-BUILDER).

This improves:

. Build scalability
. Performance efficiency
. Separation of concerns between Controller and Agent
