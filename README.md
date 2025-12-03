# Simplified-CICD-GitOps-with-Jenkins-and-ArgoCD
  
[![AWS Badge](https://img.shields.io/badge/Amazon_AWS-FFA500.svg?style=for-the-badge&logo=amazonaws&logoColor=white)](https://aws.amazon.com/)
[![GitHub Badge](https://img.shields.io/badge/GitHub-181717.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/)
[![Docker Badge](https://img.shields.io/badge/Docker-2496ED.svg?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/) 
[![ArgoCD Badge](https://img.shields.io/badge/ArgoCD-222222.svg?style=for-the-badge&logo=argocd&logoColor=white)](https://argoproj.github.io/argo-cd/)
[![Jenkins Badge](https://img.shields.io/badge/Jenkins-D24939.svg?style=for-the-badge&logo=jenkins&logoColor=white)](https://www.jenkins.io/)
[![Kubernetes Badge](https://img.shields.io/badge/Kubernetes-326CE5.svg?style=for-the-badge&logo=kubernetes&logoColor=white)](https://kubernetes.io/)
[![SonarQube Badge](https://img.shields.io/badge/SonarQube-4E9BCD.svg?style=for-the-badge&logo=sonarqube&logoColor=white)](https://www.sonarqube.org/)
[![Maven Badge](https://img.shields.io/badge/Maven-C71A36.svg?style=for-the-badge&logo=apache-maven&logoColor=white)](https://maven.apache.org/)

![non](https://github.com/kiranbakale/Simplified-CICD-GitOps-with-Jenkins-and-ArgoCD/assets/46279617/0bfb78ce-28f4-49c6-b6f3-be300bddc9dc)



## Overview

This repository demonstrates a comprehensive Continuous Integration and Continuous Deployment (CI/CD) setup using popular DevOps tools, emphasizing a GitOps approach. The tech stack includes AWS, Kubernetes (K8s), ArgoCD, Jenkins, SonarQube, Maven, Docker, and DockerHub.

## Folder Structure

- **/spring-boot-app**: Contains the source code of the application.
- **/spring-boot-app-manifests**: Includes Kubernetes deployment manifest files.

## ⚠️ Note on Repository Structure
While GitOps best practices often recommend separate repositories for code and manifests, this project takes a deliberate approach by consolidating both in a single repository. The intention is to simplify the learning experience, especially for beginners, and highlight the integral role of Argo CD in the continuous deployment process.


## CI/CD Flow

1. **Developer's Commit**: Developers commit their code to the GitHub repository.
2. **Jenkins Pipeline Trigger**: A Jenkins CI/CD pipeline is triggered automatically through the GitHub webhook.
3. **Code Analysis with SonarQube**: The pipeline performs code analysis using SonarQube to ensure code quality.
4. **Maven Build**: Maven is utilized to download required packages, build the application, and generate artifacts.
5. **Docker Containerization**: The application is containerized using Docker, and the Docker image is built.
6. **DockerHub Push**: The Docker image is pushed to DockerHub, ensuring availability and versioning.
7. **ArgoCD Image Updater**: ArgoCD's image updater component updates the image name in the repository.
8. **ArgoCD Deployment**: ArgoCD, the continuous delivery tool, orchestrates changes in the Kubernetes deployment based on the new image.

If you are interested in deploying this setup, follow the detailed step-by-step guide in this <a href="https://medium.com/@kiranbakale9/simplified-ci-cd-gitops-with-jenkins-and-argocd-b76de1c80362">Medium Article</a>
This repository serves as a blueprint for implementing a GitOps-centric CI/CD pipeline, promoting automation and efficiency in the software delivery process. Feel free to customize and extend it based on your specific project needs.

CHAPTER 1 — INTRODUCTION TO DEVOPS 

1.1 What is DevOps? 

DevOps is a combination of Development and Operations practices aimed at improving: 

Software delivery speed 

Collaboration between teams 

Reliability of production systems 

Automation of the entire software lifecycle 

DevOps replaces traditional siloed development and operations teams with a unified pipeline where: 

Developers build, test, commit code 

Operations automate infrastructure, deployment, monitoring 

Both collaborate continuously 

 

1.2 Why DevOps? 

Organizations use DevOps to: 

Reduce deployment time 

Increase release frequency 

Ensure higher quality code 

Improve system availability 

Reduce human errors through automation 

DevOps introduces standardized processes for: 

Continuous Integration (CI) 

Continuous Delivery (CD) 

Infrastructure as Code (IaC) 

Automated testing 

Monitoring & logging 

 

1.3 Key DevOps Principles 

The core pillars of DevOps include: 

Automation — minimize manual tasks 

Collaboration — developers + operations together 

Continuous improvement — frequent small updates 

Fast feedback loops — detect failures early 

Infrastructure as Code — automated provisioning 

Monitoring — observe systems continuously 

 

1.4 DevOps Toolchain 

Companies adopt a series of tools to automate the workflow: 

Git, GitHub 

Jenkins 

Docker 

Kubernetes 

SonarQube 

Trivy 

JFrog Artifactory 

Argo CD (GitOps) 

Each tool plays a specific role in the CI/CD pipeline. 

 

CHAPTER 2 — INTRODUCTION TO DEVSECOPS 

2.1 What is DevSecOps? 

DevSecOps is DevOps with integrated security at every stage of the pipeline. 

Traditional DevOps adds security late in the cycle. 

 DevSecOps shifts it left by including security checks during: 

Code building 

Code scanning 

Container scanning 

Repository management 

Deployment policy enforcement 

 

2.2 Why DevSecOps? 

It ensures: 

Early vulnerability detection 

Compliance with standards 

Secure Docker images 

Secure code quality 

Secure cluster deployments 

Zero-trust CI/CD pipelines 

This aligns development, operations, and security into one cycle. 

 

2.3 Where Security is Applied in Your Pipeline 

Your project includes security at: 

SonarQube Scan 

 Static code analysis 

Trivy FS Scan 

 Source code vulnerability scanning 

Trivy Image Scan 

 Container scanning 

JFrog Artifactory 

 Secure artifact storage 

ArgoCD GitOps 

 Prevent unauthorized cluster changes 

This ensures complete DevSecOps coverage. 

 

CHAPTER 3 — CI/CD OVERVIEW 

3.1 What is CI (Continuous Integration)? 

CI automates: 

Merging code 

Building 

Testing 

Scanning 

Packaging 

Every push triggers a pipeline that ensures the code is: 

Functionally correct 

Secure 

High quality 

Build-ready 

 

3.2 What is CD (Continuous Delivery / Deployment)? 

CD automates deployment of built artifacts into Kubernetes or production. 

Your project uses GitOps-based Continuous Deployment through ArgoCD. 

The deployment pipeline: 

Automatically updates YAML in a Git repo 

ArgoCD syncs and applies changes to Kubernetes 

 

3.3 Why CI/CD? 

Benefits: 

Faster releases 

Minimal human errors 

Repeatable environments 

Early bug detection 

Higher security 

Version-controlled deployments 

CI/CD is the standard for modern DevOps teams. 

 

CHAPTER 4 — GITOPS OVERVIEW 

4.1 What is GitOps? 

GitOps is a methodology where Git is the single source of truth for the entire deployment state. 

Instead of Jenkins pushing YAML to Kubernetes, GitOps uses: 

A deployment repo 

A GitOps operator (ArgoCD) 

A pull-based deployment approach 

 

4.2 GitOps Principles 

Desired state is always stored in Git. 

Changes in Git trigger deployments. 

Operators continuously sync clusters. 

Clusters are self-healing. 

 

4.3 Why GitOps? 

GitOps provides: 

Version-controlled deployments 

Auditability 

Instant rollback 

Strong security (no CI access to cluster) 

Automation 

This fits perfectly with Kubernetes environments. 

 

CHAPTER 5 — TOOLS OVERVIEW 

You are using a complete DevSecOps toolchain: 

GitHub (Version control) 

Jenkins (CI engine) 

Maven (Build tool) 

SonarQube (Code quality scanning) 

Trivy (Security scanner) 

JFrog Artifactory (Artifact repository) 

Docker (Container engine) 

Kubernetes (Orchestration) 

ArgoCD (GitOps CD engine) 

Kustomize (Resource composition) 

CHAPTER 6 — CI ARCHITECTURE 

6.1 Overview of Your CI Pipeline 

Your Continuous Integration (CI) system is built using Jenkins, integrating: 

GitHub (source code) 

Maven (build) 

SonarQube (code quality scan) 

Trivy (security scan) 

JFrog Artifactory (artifact storage) 

Docker (image build) 

DockerHub (image push) 

GitOps (update deployment repo) 

The pipeline is fully automated and sequential. 

 

6.2 CI Architecture Diagram (Text-Based) 

               ┌────────────────────┐ 
                │     GitHub Repo    │ 
                │ (Source Code Push) │ 
                └─────────┬──────────┘ 
                          ↓ 
                ┌────────────────────┐ 
                │       Jenkins       │ 
                │     (CI Engine)     │ 
                └─────────┬──────────┘ 
       ┌───────────────────┼───────────────────────┐ 
       ↓                   ↓                       ↓ 
┌────────────┐     ┌──────────────┐        ┌─────────────────┐ 
│ Maven Build│     │ SonarQube     │        │ Trivy FS Scan    │ 
└────────────┘     └──────────────┘        └─────────────────┘ 
       ↓                                           ↓ 
┌──────────────────────┐                    ┌───────────────────────┐ 
│ JAR Upload to JFrog  │                    │ Docker Build          │ 
│ (Artifact Mgmt)      │                    └───────────────────────┘ 
└──────────────────────┘                               ↓ 
                                                ┌──────────────┐ 
                                                │ Trivy Image  │ 
                                                │ Vulnerability│ 
                                                └──────────────┘ 
                                                         ↓ 
                                                ┌─────────────────┐ 
                                                │ DockerHub Push    
                                                └────────────────── 
                                                         ↓ 
                                         ┌───────────────────────── 
                                         │ Update CD Repo (GitOps)     
                                         │ deployment.yaml             
                                         └─────────────────────── 
  

 

6.3 CI Pipeline Flow Summary 

Developer pushes code to GitHub 

Jenkins fetches code 

Maven builds & packages JAR 

SonarQube performs static code analysis 

Trivy scans filesystem for vulnerabilities 

JAR is pushed to JFrog Artifactory 

Docker image is built 

Trivy scans Docker image 

Image is pushed to DockerHub 

Jenkins updates the GitOps CD repo 

ArgoCD deploys automatically (pull-based) 

 

6.4 Why This CI Architecture is Enterprise-Standard 

Code builds are reproducible 

Artifacts are versioned securely 

Containers go through security scanning 

Deployment is decoupled from CI for safety 

GitOps avoids direct cluster modification 

Every stage enforces DevSecOps principles 

This matches the DevSecOps maturity model. 

 

CHAPTER 7 — CI WORKFLOW (FINAL VERSION) 

This chapter documents the updated CI workflow you finalized. 

7.1 Final CI Workflow Sequence 

Pull Code from GitHub 

Build using Maven 

SonarQube Scan 

Trivy FS Scan 

Upload JAR to JFrog Maven Repo 

Docker Build 

Trivy Image Scan 

Push Docker Image to DockerHub 

Update GitOps Deployment Repository 

Archive Reports 

This is the complete DevSecOps-integrated CI flow. 

 

7.2 Why This CI Workflow is Perfect for DevSecOps 

Code quality checks early (SonarQube) 

Security scanning at code and container level (Trivy) 

Immutable artifacts stored in JFrog 

Docker-based deployments for Kubernetes 

GitOps ensures safe & auditable CD 

This ensures a secure, consistent, end-to-end delivery process. 

 

CHAPTER 8 — JENKINS INSTALLATION & SETUP 

This chapter covers complete Jenkins installation, configuration, plugins, user access, and preparation for the CI pipeline. 

 

8.1 What is Jenkins? 

Jenkins is an open-source Continuous Integration (CI) automation server. 

It automates: 

Pulling source code 

Building applications 

Scanning code quality 

Security scanning 

Building Docker images 

Pushing artifacts/images 

Triggering GitOps workflow 

Your DevSecOps project uses Jenkins as the central CI engine. 

 

8.2 Why DevOps Engineers Use Jenkins 

Highly extensible with plugins 

Supports all languages (Java, Go, Python, etc.) 

Integrates easily with GitHub, SonarQube, Trivy, Docker 

Designed for pipeline-as-code (Jenkinsfile) 

Runs on Linux (Ubuntu EC2) 

Open-source and enterprise-ready 

 

8.3 Installation Steps (Ubuntu 22.04) 

Run the following commands on your Jenkins EC2 server. 

Step 1 — Install Java 17 

sudo apt update -y 
sudo apt install -y openjdk-17-jdk 
  

Step 2 — Add Jenkins Package Repo 

curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | sudo tee \ 
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null 
 
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian binary/" | \ 
  sudo tee /etc/apt/sources.list.d/jenkins.list 
  

Step 3 — Install Jenkins 

sudo apt update -y 
sudo apt install -y jenkins 
  

Step 4 — Start Jenkins 

sudo systemctl enable jenkins 
sudo systemctl start jenkins 
sudo systemctl status jenkins 
  

Step 5 — Get Initial Admin Password 

sudo cat /var/lib/jenkins/secrets/initialAdminPassword 
  

Access Jenkins at: 

http://<EC2-PUBLIC-IP>:8080 
  

 

8.4 Installing Required Plugins 

Go to: 

 Manage Jenkins → Manage Plugins → Available 

Install: 

Pipeline 

Git 

GitHub Branch Source 

Credentials Binding 

Docker Pipeline 

SonarQube Scanner 

JFrog Plugin (optional, curl-based upload is also supported) 

HTML Publisher 

Pipeline Utility Steps 

These plugins enable full CI functionality. 

 

8.5 Add Jenkins to Docker Group 

Jenkins needs Docker privileges to build and push images. 

Run: 

sudo usermod -aG docker jenkins 
sudo systemctl restart jenkins 
  

8.6 Required Jenkins Credentials 

Go to: 

 Jenkins Dashboard → Manage Jenkins → Credentials → Global 

Create the following credentials: 

1. sonar-token 

Type: Secret text 

Value: SonarQube token 

2. sonar-url 

Type: Secret text 

Value example: 

http://YOUR_EC2_PUBLIC_IP:9000 
  

3. artifactory-url 

Type: Secret text 

Example: 

http://YOUR_EC2_PUBLIC_IP:8081/artifactory 
  

4. artifactory-creds 

Type: Username with password 

For uploading JAR artifacts 

5. docker 

Type: Username with password 

DockerHub credentials 

6. github-creds 

Type: Username with password or PAT token 

Full GitOps integration 

These credentials will be used inside your Jenkinsfile. 

 

8.7 Jenkins URL Configuration 

Recommended (optional): 

Go to: 

 Manage Jenkins → Configure System 

Set: 

Jenkins URL: http://<EC2-PUBLIC-IP>:8080 
  

 

8.8 Jenkins Node Preparation 

Ensure these commands work on Jenkins: 

docker --version 
trivy --version 
mvn -version 
  

If not installed, install: 

sudo apt install -y maven 
  

 

8.9 Jenkins Folder Structure for Your Project 

Your project repo: 

Devsecops-aayush/ 
  ├── java-maven-sonar-argocd-helm-k8s/ 
  │     └── spring-boot-app (Maven project) 
  └── Jenkinsfile 
  

This structure integrates perfectly with your pipeline. 

 

8.10 Jenkins Global Security 

Make sure: 

Anonymous access = Off 

Logged-in access = On 

CSRF protection = Enabled 

 

8.11 Jenkinsfile Overview 

Your Jenkinsfile is stored at root of CI repo: 

Devsecops-aayush/Jenkinsfile 
  

The next chapters will cover the full Jenkinsfile explanation. 

 

 

 

CHAPTER 9 — REQUIRED JENKINS PLUGINS 

To run your complete DevSecOps CI pipeline, Jenkins must have specific plugins installed. 

 This chapter lists every required plugin, why it’s needed, and how it’s used in your pipeline. 

 

9.1 Plugin Installation Path 

Navigate in Jenkins: 

Manage Jenkins → Manage Plugins → Available 
  

Search and install the following plugins. 

 

9.2 Essential Plugins List 

1. Pipeline Plugin 

Purpose: 

 Enables Jenkinsfile-based CI/CD pipelines. 

Why your project needs it: 

 Your entire CI is written using a declarative pipeline. 

 

2. Git Plugin 

Purpose: 

 Allows Jenkins to pull code from Git repositories. 

Used in your pipeline: 

 Stage: "Pull Code" 

 

3. GitHub Branch Source Plugin 

Purpose: 

 Provides integration with GitHub organizations and repositories. 

Why it’s needed: 

 For GitHub webhook triggers 

 (automatic pipeline runs on commits). 

 

4. Credentials Binding Plugin 

Purpose: 

 Injects credentials into pipeline environment variables. 

Used for: 

DockerHub 

GitHub (PAT) 

Artifactory 

SonarQube token 

URLs 

 

5. Docker Pipeline Plugin 

Purpose: 

 Allows building and pushing Docker images in pipelines. 

Used in your pipeline: 

Docker Build 

DockerHub Push 

Trivy Image Scan 

 

6. Pipeline Utility Steps 

Purpose: 

 Useful file management and text manipulation. 

Used in GitOps stage (optional). 

 

7. SonarQube Scanner Plugin 

Purpose: 

 Integrates SonarQube with Jenkins. 

Used in your pipeline: 

 Stage: "SonarQube Scan" 

 

8. HTML Publisher Plugin 

Purpose: 

 Publishes HTML reports generated during pipeline runs. 

Used with: 

Trivy HTML image scan report 

 

9. JFrog Artifactory Plugin (optional) 

Purpose: 

 Integrates JFrog repositories with Jenkins. 

Note: 

 Your pipeline uses curl for JAR upload, which is fully acceptable and often simpler. 

 Plugin not mandatory. 

 

10. Blue Ocean (optional) 

Purpose: 

 Modern UI for visualizing pipelines. 

Not required, but useful. 

 

9.3 Recommended Plugin Order 

Install plugins in this order: 

Pipeline 

Git + GitHub Branch Source 

Credentials Binding 

Docker Pipeline 

SonarQube Scanner 

HTML Publisher 

This prevents dependency errors. 

 

9.4 Verify Installation 

Go to: 

Manage Jenkins → Manage Plugins → Installed 
  

Ensure all plugins appear without warnings. 

 

9.5 After Plugins Are Installed 

You must configure: 

SonarQube server 

Docker permissions 

Global credentials 

Jenkinsfile at repo root 

These are covered in the next chapters. 

 

CHAPTER 10 — JENKINS CREDENTIALS SETUP 

Jenkins credentials are critical for securely connecting to external tools such as GitHub, DockerHub, SonarQube, and Artifactory. 

 Your CI pipeline depends heavily on these credentials to run successfully. 

This chapter provides a complete list of credentials, why each is needed, how to create them, and how Jenkinsfile uses them. 

 

10.1 Where to Create Credentials 

Navigate to: 

Jenkins Dashboard  
→ Manage Jenkins 
→ Credentials 
→ System 
→ Global credentials (unrestricted) 
  

Click: 

Add Credentials 
  

Choose the correct type for each. 

 

10.2 Full List of Required Credentials 

The following credentials MUST exist exactly with the IDs used in your Jenkinsfile: 

 

1. sonar-token 

Type: Secret text 

 Value: Token generated from SonarQube UI 

 Used in Jenkinsfile for: 

 SonarQube authentication during code scan. 

Jenkinsfile reference: 

SONAR_AUTH = credentials('sonar-token') 
  

 

2. sonar-url 

Type: Secret text 

 Value example: 

http://<EC2-IP>:9000 
  

Used for: 

SONAR_URL = credentials('sonar-url') 
  

 

3. artifactory-url 

Type: Secret text 

 Value example: 

http://<EC2-IP>:8081/artifactory 
  

Used for uploading JAR files. 

 

4. artifactory-creds 

Type: Username with Password 

 Username: Artifactory service user 

 Password: Artifactory password 

Used for JAR upload: 

curl -u ${ARTIFACTORY_CREDS_USR}:${ARTIFACTORY_CREDS_PSW} 
  

 

5. docker 

Type: Username with Password 

 Value: DockerHub account 

 Purpose: 

 Push Docker image to DockerHub. 

Used as: 

DOCKERHUB_CREDS = credentials('docker') 
  

 

6. github-creds 

Type: Username with Password 

 OR 

 Type: Personal Access Token (preferred) 

Purpose: 

 Allows Jenkins to push updates to GitOps deployment repo. 

Used here: 

GIT_CREDS = credentials('github-creds') 
  

 

10.3 Naming Credentials Correctly 

Credential IDs must match exactly the names used in the Jenkinsfile: 

Credential ID 

Type 

Purpose 

sonar-token 

Secret text 

Sonar authentication 

sonar-url 

Secret text 

Sonar URL 

artifactory-url 

Secret text 

Artifactory base URL 

artifactory-creds 

Username with password 

Upload JAR 

docker 

Username with password 

DockerHub login 

github-creds 

Username/password or PAT 

Push updates to GitOps repo 

If IDs mismatch, pipeline will fail at environment stage. 

 

10.4 Minimal Credential Security Policy 

Do not store plain passwords in Jenkinsfile 

Never echo passwords in logs 

Always use Jenkins credential binding 

Use least-privilege accounts where possible 

Change passwords regularly 

 

10.5 Validate Credentials 

You should manually validate: 

GitHub credentials: 

git clone https://USERNAME:PASSWORD@github.com/<repo>.git 
  

DockerHub credentials: 

docker login 
  

Artifactory credentials: 

curl -u user:pass <artifactory-url> 
  

Sonar token: 

Test by: 

curl -u <token>: http://<EC2-IP>:9000/api/system/status 
  

 

10.6 Credentials in the Jenkinsfile (Your Final Version) 

Below is the extracted environment block from your final Jenkinsfile: 

environment { 
    SONAR_AUTH = credentials('sonar-token') 
    SONAR_URL = credentials('sonar-url') 
 
    ARTIFACTORY_URL = credentials('artifactory-url') 
    ARTIFACTORY_CREDS = credentials('artifactory-creds') 
 
    DOCKERHUB_CREDS = credentials('docker') 
    GIT_CREDS = credentials('github-creds') 
 
    IMAGE_NAME = "aayush-devsecops" 
    DEPLOY_REPO = "https://github.com/Aayushgit18/Devsecops-aayush.git" 
} 
  

All IDs in bold must be present exactly. 

 

CHAPTER 11 — MAVEN BUILD STAGE 

The Maven Build Stage is the foundation of your CI pipeline. 

 It compiles the Java application, resolves dependencies, runs packaging, and produces the final .jar file required for deployment and artifact storage. 

This chapter explains: 

What Maven is 

Why DevOps engineers use it 

How it works in your pipeline 

Detailed explanation of your Maven commands 

Output of the build stage 

 

11.1 What is Maven? 

Maven is a Java build automation and dependency management tool. 

It handles: 

Compilation 

Dependency resolution 

Unit testing 

Packaging JAR/WAR files 

Project structure standardization 

Maven understands your project through: 

pom.xml 
  

 

11.2 Why Maven in DevOps and CI? 

DevOps teams prefer Maven because: 

It is deterministic (same input → same output) 

Standard project structure (src/main/java, etc.) 

Integrates perfectly with Jenkins 

Works smoothly with SonarQube 

Produces versioned JAR artifacts 

Easy to run via command line 

Your pipeline depends on Maven to generate the artifact used later in: 

Artifactory upload 

Docker image build 

 

11.3 Installing Maven 

On Jenkins EC2: 

sudo apt install -y maven 
mvn -version 
  

Ensure Jenkins user has access to Maven binary. 

 

11.4 Maven Build Stage from Your Jenkinsfile 

Below is your actual stage: 

stage('Maven Build') { 
    steps { 
        sh ''' 
            cd java-maven-sonar-argocd-helm-k8s/spring-boot-app 
            mvn clean package -DskipTests 
        ''' 
    } 
} 
  

 

11.5 Explanation of Each Command 

1. Change directory 

cd java-maven-sonar-argocd-helm-k8s/spring-boot-app 
  

Moves into your Spring Boot project folder. 

 

2. Maven Clean 

mvn clean 
  

Deletes: 

target/ directory 

compiled .class files 

leftover build artifacts 

This ensures a fresh, reproducible build. 

 

3. Maven Package 

mvn package 
  

Runs: 

compile 

test (skipped here) 

create JAR 

Final output is stored in: 

target/*.jar 
  

 

4. Skip Tests Option 

-DskipTests 
  

Used because: 

Speeds up CI builds 

Tests may not be configured 

Optional in learning environments 

In production, use: 

-DskipTests=false 
  

 

11.6 Result of Maven Build Stage 

If successful: 

A JAR file is created (application artifact) 

Build status in Jenkins turns green 

The JAR becomes eligible for: 

Sonar scan 

Artifactory upload 

Image build in Docker 

This JAR is the core artifact for your CI→CD process. 

 

11.7 Most Common Maven Issues & Fixes 

Issue 1: Java version mismatch 

Fix: 

sudo update-alternatives --config java 
  

Issue 2: Missing dependencies 

Fix: 

mvn dependency:resolve 
  

Issue 3: Build failure due to old files 

Fix: 

mvn clean package 
  

 

11.8 Jenkins Build Artifacts 

Jenkins typically archives: 

target/*.jar 
  

Later, JFrog Artifactory uses this file. 

 

This completes the Maven Build chapter. 

 

When ready: 

Send “next” to continue to 

CHAPTER 12 — SonarQube Scan Stage 

 

 

CHAPTER 12 — SONARQUBE SCAN STAGE 

SonarQube is one of the most important tools in a DevSecOps CI pipeline. 

 This chapter explains the complete SonarQube integration used in your pipeline: 

What SonarQube is 

Why DevOps teams use it 

How SonarQube enforces quality gates 

How you installed SonarQube 

How to integrate Sonar with Jenkins 

Your exact SonarQube scan stage from the Jenkinsfile 

Detailed explanation of every step 

 

12.1 What is SonarQube? 

SonarQube is a Static Application Security Testing (SAST) platform. 

It performs: 

Code quality analysis 

Bug detection 

Vulnerability scanning 

Code smell detection 

Duplicate code detection 

Maintainability checks 

Clean code enforcement 

It provides dashboards for: 

Quality Gates 

Bugs 

Vulnerabilities 

Security Hotspots 

Coverage 

Duplications 

 

12.2 Why DevOps Engineers Use SonarQube 

DevOps teams rely on SonarQube to: 

Detect issues before deployment 

Ensure code follows standards 

Reduce technical debt 

Improve maintainability 

Enforce security rules 

Prevent unsafe code from reaching production 

Your CI pipeline uses Sonar early to shift security left. 

 

12.3 SonarQube Installation (Docker Compose) 

You installed SonarQube with PostgreSQL using: 

docker-compose up -d 
  

Ports: 

9000 → SonarQube UI 
  

Login: 

admin / admin 
  

Post-install requirement: 

Create a token for Jenkins from: 

 My Account → Security → Generate Token 

 

12.4 Jenkins → SonarQube Integration 

Go to: 

Manage Jenkins → Configure System → SonarQube Server 
  

Add: 

Name: SonarQube 

 Server URL: 

http://<EC2-IP>:9000 
  

Authentication token: 

 Use credential sonar-token 

 

12.5 Sonar Scanner in Jenkins (Internal Maven Scanner) 

No external scanner needed. 

 You use Maven’s built-in sonar goal: 

mvn sonar:sonar 
  

This automatically uploads analysis results to SonarQube. 

 

12.6 Your SonarQube Stage in Jenkinsfile 

Final Version: 

stage('SonarQube Scan') { 
    steps { 
        sh ''' 
            cd java-maven-sonar-argocd-helm-k8s/spring-boot-app 
            mvn sonar:sonar \ 
              -Dsonar.projectKey=devsecops-aayush \ 
              -Dsonar.host.url=${SONAR_URL} \ 
              -Dsonar.token=${SONAR_AUTH} 
        ''' 
    } 
} 
  

 

12.7 Explanation of Each Parameter 

-Dsonar.projectKey=devsecops-aayush 

This uniquely identifies your project in SonarQube. 

Created under: 

Projects → Create Project → Manual 
  

 

-Dsonar.host.url=${SONAR_URL} 

Jenkins credential containing: 

http://<EC2-IP>:9000 
  

 

-Dsonar.token=${SONAR_AUTH} 

Authentication token securely stored in Jenkins Credentials. 

 

12.8 Quality Gates 

SonarQube will check: 

Bugs = 0 

Security Vulnerabilities = 0 

Code Smells minimal 

No duplicated code 

Maintainability rating good 

Coverage not enforced (optional) 

Pipeline may be configured to fail if gates fail (optional). 

 

12.9 SonarQube Scan Output 

After running scan: 

Dashboard created 

Issue categories show 

Code smells visible 

Bug sections updated 

Security hotspots displayed 

History maintained 

This improves code quality and reduces risk. 

 

12.10 Common SonarQube Issues 

Issue 

Cause 

Fix 

Authentication error 

Wrong token 

Regenerate token 

Cannot connect to server 

Wrong URL 

Check SONAR_URL credential 

“Project not found” 

Wrong project key 

Update sonar.projectKey 

Scan fails due to Java version 

Wrong JDK 

Use Java 17 

 

This completes the SonarQube Scan chapter. 

 

 

CHAPTER 13 — TRIVY FILESYSTEM (FS) SCAN STAGE 

Trivy is the security backbone of your DevSecOps pipeline. 

 This chapter explains how Trivy FS scan works, why DevSecOps engineers use it, how it integrates with Jenkins, and how your pipeline executes it. 

 

13.1 What is Trivy? 

Trivy is an open-source vulnerability scanner for: 

Filesystem (source code scanning) 

Docker images 

Git repositories 

Kubernetes manifests 

SBOM scanning 

It detects: 

Vulnerabilities (CVEs) 

Misconfigurations 

Secrets 

Insecure dependencies 

 

13.2 Why DevSecOps Uses Trivy FS Scan 

Trivy FS scan is used to scan your source code directory before building the application. 

It detects: 

Hardcoded credentials 

Vulnerable libraries 

Misconfiguration in YAML/JSON 

Insecure configuration files 

Sensitive information leakage 

Bad Dockerfile practices 

This achieves shift-left security. 

 

13.3 Installing Trivy 

On Jenkins EC2: 

wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add - 
echo deb https://aquasecurity.github.io/trivy-repo/deb stable main | sudo tee /etc/apt/sources.list.d/trivy.list 
sudo apt update -y 
sudo apt install -y trivy 
  

Verify: 

trivy --version 
  

 

13.4 Trivy FS Scan in Your Pipeline 

Your Jenkinsfile contains this stage: 

stage('Trivy FS Scan') { 
    steps { 
        sh ''' 
            trivy fs java-maven-sonar-argocd-helm-k8s --exit-code 0 --format table 
        ''' 
    } 
} 
  

 

13.5 Explanation of Your Trivy Commands 

Command: 

trivy fs java-maven-sonar-argocd-helm-k8s 
  

Trivy scans the entire directory: 

java-maven-sonar-argocd-helm-k8s/ 
  

This includes: 

Java code 

Dockerfiles 

YAML files 

Configurations 

Secrets 

Node modules (if present) 

Dependency files 

 

13.6 Flag Breakdown 

--exit-code 0 

Even if vulnerabilities exist: 

Pipeline should not fail 

You continue to build for learning/dev environment 

In production, recommended: 

--exit-code 1 
  

To fail on HIGH and CRITICAL vulnerabilities. 

 

--format table 

Scan output appears in clean table format. 

 

13.7 What FS Scan Detects 

Trivy FS scan checks: 

CVEs in package-lock.json, requirements.txt, JARs 

Secrets in files 

Misconfigured Dockerfiles 

Misconfigured Kubernetes YAML 

Hardcoded passwords 

AWS or GitHub tokens 

Sensitive keys 

Shell script vulnerabilities 

This is crucial for preventing breaches. 

 

13.8 Output of FS Scan Stage 

Sample output includes: 

Vulnerability ID 

Package Name 

Severity 

Installed Version 

Fixed Version 

Your Jenkins pipeline will display this in the console output. 

 

13.9 Recommended Best Practices 

Always store FS scan report in Jenkins: 

archiveArtifacts 'trivy-fs-report.txt' 
  

Fail pipeline on high severity (optional): 

--severity HIGH,CRITICAL --exit-code 1 
  

Include Trivy in PR checks (optional): 

 Run Trivy on GitHub Actions before merging. 

 

13.10 Typical Issues & Fixes 

Issue: “Database update failed” 

Fix: 

trivy --debug fs <path> 
  

or ensure outbound internet access. 

Issue: Too many findings 

Fix: Create .trivyignore. 

Issue: Pipeline fails unexpectedly 

Fix: Ensure --exit-code 0. 

 

This completes the Filesystem Scan chapter. 

 

 

 

CHCHAPTER 14 — UPLOADING JAR TO JFROG ARTIFACTORY 

Artifactory is the heart of artifact management in your DevSecOps pipeline. 

 This chapter covers: 

What Artifactory is 

Why DevOps engineers use it 

How you installed it 

How Maven/JAR upload works 

Detailed breakdown of your Jenkins stage 

JAR versioning logic 

How artifacts integrate with GitOps and CD 

 

14.1 What is JFrog Artifactory? 

JFrog Artifactory is a universal artifact repository that stores: 

Build artifacts (JAR, WAR) 

Docker images 

Helm charts 

npm, PyPI packages 

Generic binaries 

It supports local, remote, and virtual repositories. 

 

14.2 Why DevOps Engineers Use Artifactory 

DevOps teams rely on Artifactory because: 

Artifacts must be versioned 

Builds must be stored securely 

CI/CD pipelines need reproducible builds 

Docker images & JAR files must be traceable 

Remote repositories cache dependencies 

Enterprise build promotion is easier 

Artifactory ensures a single place for artifact lifecycle management. 

 

14.3 Artifactory Installed in Your Setup 

You installed Artifactory OSS using Docker Compose: 

Ports: 

8081 → Web UI 
8082 → Docker registry 
  

Repositories created: 

maven-repo (local maven repository) 

docker-local (optional for Docker registry; you push to DockerHub in your case) 

 

14.4 Overview of the JAR Upload Stage in Pipeline 

Your Jenkins pipeline uploads the JAR produced during Maven build to Artifactory to store it as a versioned artifact. 

This ensures: 

Every build has a record 

Artifacts are not lost 

Artifacts match image version 

Reproducibility 

 

14.5 Your Pipeline Stage (Final Version) 

stage('Upload JAR to JFrog Maven Repo') { 
    steps { 
        sh ''' 
            JAR_FILE=$(find java-maven-sonar-argocd-helm-k8s -name "*.jar" | head -1) 
            VERSIONED_JAR=spring-boot-web-b${BUILD_NUMBER}.jar 
 
            cp $JAR_FILE $VERSIONED_JAR 
 
            curl -u ${ARTIFACTORY_CREDS_USR}:${ARTIFACTORY_CREDS_PSW} \ 
             -T $VERSIONED_JAR \ 
             ${ARTIFACTORY_URL}/maven-repo/ 
        ''' 
    } 
} 
  

 

14.6 Step-by-Step Breakdown 

Step 1 — Locate the JAR 

JAR_FILE=$(find java-maven-sonar-argocd-helm-k8s -name "*.jar" | head -1) 
  

Searches the entire directory for .jar file. 

 

Step 2 — Version the JAR 

VERSIONED_JAR=spring-boot-web-b${BUILD_NUMBER}.jar 
  

If Jenkins BUILD_NUMBER = 14 

 Then output JAR becomes: 

spring-boot-web-b14.jar 
  

This ensures unique artifact versioning. 

 

Step 3 — Copy file 

cp $JAR_FILE $VERSIONED_JAR 
  

Renames the original JAR to the versioned JAR. 

 

Step 4 — Upload to Artifactory using curl 

curl -u USER:PASS -T file http://X.X.X.X:8081/artifactory/maven-repo/ 
  

-T uploads a binary file. 

Artifactory Path: 

<maven-local-repo-url>/ 
  

 

14.7 Why Use curl Instead of Maven deploy? 

You chose the simplest method for learning environment: 

No need to configure settings.xml 

Faster and easier to debug 

Works without Maven credentials setup 

In production, teams use: 

mvn deploy 
  

With a full settings.xml configuration. 

 

14.8 Confirming Upload in UI 

Access: 

http://<EC2-IP>:8081/ui 
  

Navigate: 

Artifacts → maven-repo 
  

You should see: 

spring-boot-web-b<number>.jar 
  

Every CI run adds a new version. 

 

14.9 Common Issues & Fixes 

Problem 

Cause 

Fix 

401 unauthorized 

Wrong creds 

Check artifactory-creds 

404 repo not found 

Wrong repo name 

Use correct repoKey 

file locked 

Old corrupt file 

Delete manually 

Connection refused 

Port blocked 

Open SG ports 

 

14.10 Artifacts and GitOps 

Artifacts are separate from deployments. 

Meaning: 

Git (deployment repo) stores YAML 

Artifactory stores JAR 

DockerHub stores images 

This separation improves: 

Security 

Scalability 

Compliance 

 

This finishes the Artifactory JAR Upload chapter. 

 

 

 

CHAPTER 15 — DOCKER BUILD STAGE 

The Docker Build Stage converts your Spring Boot application (JAR) into a containerized application that can be deployed on Kubernetes. 

 This chapter explains: 

What Docker is 

Why DevOps engineers use it 

How your pipeline builds the Docker image 

How versioning works 

How Docker integrates into GitOps + ArgoCD 

Best practices 

 

15.1 What is Docker? 

Docker is a containerization platform that packages applications into: 

Lightweight 

Portable 

Immutable 

Fast-starting 

containers that run the same in every environment. 

In DevOps, Docker solves: 

“Works on my machine” issues 

Dependency conflicts 

Slow deployments 

Environment drift 

 

15.2 Why Containers in DevSecOps? 

Containers allow: 

Immutable deployment artifacts 

Secure scanning of images 

Portability between dev → stage → prod 

Simplified Kubernetes deployment 

Separation from host machine 

Faster CI pipelines 

Your CI/CD pipeline relies heavily on Docker because Kubernetes (your CD system) only runs containers. 

 

15.3 Docker in Your CI Pipeline 

Your pipeline: 

Builds a Docker image using the Dockerfile 

Tags the image with the Jenkins build number 

Scans the image using Trivy 

Pushes the secure image to DockerHub 

Updates the GitOps repo with the new image 

ArgoCD deploys it 

 

15.4 Dockerfile (inside your project) 

Inside: 

java-maven-sonar-argocd-helm-k8s/spring-boot-app/ 
  

You should have a Dockerfile similar to: 

FROM openjdk:17-jdk-slim 
COPY target/*.jar app.jar 
ENTRYPOINT ["java", "-jar", "/app.jar"] 
  

This type of Dockerfile: 

Uses an official OpenJDK base image 

Copies your application into container 

Starts app using ENTRYPOINT 

 

15.5 Docker Installation on Jenkins EC2 

You installed Docker using: 

curl -fsSL https://get.docker.com -o get-docker.sh 
sudo sh get-docker.sh 
  

Then added Jenkins user to Docker group: 

sudo usermod -aG docker jenkins 
sudo systemctl restart jenkins 
  

This gives Jenkins permission to build images. 

 

15.6 Your Docker Build Stage (Final Version) 

stage('Docker Build') { 
    steps { 
        sh ''' 
            cd java-maven-sonar-argocd-helm-k8s/spring-boot-app 
            docker build -t ${DOCKERHUB_CREDS_USR}/${IMAGE_NAME}:b${BUILD_NUMBER} . 
        ''' 
    } 
} 
  

 

15.7 Explanation of the Docker Build Stage 

Step 1 — Enter Project Directory 

cd java-maven-sonar-argocd-helm-k8s/spring-boot-app 
  

Moves Jenkins into folder with Dockerfile. 

 

Step 2 — Build Docker Image 

docker build -t username/image-name:tag . 
  

Your final image name: 

docker.io/<dockerhub-username>/aayush-devsecops:b<BUILD_NUMBER> 
  

Example tag: 

aayush595/aayush-devsecops:b14 
  

b14 = build number 14. 

 

15.8 Why Version Images with Build Numbers? 

Advantages: 

Every build produces a unique image 

Traceable to Jenkins job 

Makes rollback easy 

Avoids overriding tags 

Works perfectly with GitOps 

Example: 

b10 
b11 
b12 
  

Each one represents a full CI cycle. 

 

15.9 Image Verification Before Push 

After build, you can verify on Jenkins node: 

docker images | grep aayush-devsecops 
  

 

15.10 Best Practices for Docker Build Stage 

Always use small base images 

 Example: openjdk:17-jdk-slim 

Pin base image versions 

Run Trivy Image Scan before pushing 

Never run as root inside container 

Scan image for vulnerabilities 

Ensure .dockerignore is configured 

 

15.11 Common Docker Build Issues & Fixes 

Issue 

Cause 

Fix 

Permission denied 

Jenkins not in docker group 

Add jenkins user to docker group 

Build context too large 

Missing .dockerignore 

Add large folders to ignore 

Dockerfile not found 

Wrong path 

cd to correct directory 

Network timeout 

EC2 outbound blocked 

Allow outbound internet access 

 

This completes the Docker Build Stage chapter. 

 

 

 

CHAPTER 16 — TRIVY DOCKER IMAGE SCAN STAGE 

This chapter explains the Docker Image Scan Stage in your CI pipeline using Trivy, which is a critical DevSecOps component. 

 You will learn: 

What Trivy Image Scan is 

Why container scanning is mandatory 

How the scan works 

How you implemented it 

How HTML reports are generated 

Best practices for production scanning 

 

16.1 What is Trivy Image Scan? 

Trivy Image Scan analyzes a Docker image for: 

Vulnerable OS packages (Alpine, Ubuntu, Debian, etc.) 

Vulnerable application dependencies (Java, Python, etc.) 

Critical CVEs (security issues) 

High severity vulnerabilities 

Malware 

Misconfigurations 

Sensitive files exposed inside the image 

This ensures your container is safe before deployment. 

 

16.2 Why DevSecOps Uses Image Scanning 

Image scanning is a mandatory step in DevSecOps because: 

Vulnerabilities inside container images can lead to attacks 

Containers often include old libraries 

Images get reused across clusters → risk spreads 

Security must shift-left 

Kubernetes is only as secure as the images it runs 

Your pipeline scans images before pushing to DockerHub. 

 

16.3 How Trivy Scans Docker Images 

Trivy checks: 

Installed packages 

System libraries 

Application libraries 

Image layers 

Configuration files 

Embedded credentials 

OpenSSL, glibc, log4j vulnerabilities 

Trivy compares against: 

CVE databases 

NVD 

GitHub Advisory 

OS Vendor advisories 

This ensures accurate and up-to-date detection. 

 

16.4 Trivy Image Scan Stage from Your Jenkinsfile 

Below is your final stage: 

stage('Trivy Docker Image Scan (HTML Only)') { 
    steps { 
        sh ''' 
            trivy image ${DOCKERHUB_CREDS_USR}/${IMAGE_NAME}:b${BUILD_NUMBER} \ 
            --severity HIGH,CRITICAL \ 
            --format template \ 
            --template @/usr/local/share/trivy/templates/html.tpl \ 
            --output trivy-image-report.html 
        ''' 
    } 
} 
  

 

16.5 Step-by-Step Explanation 

1. Image selected for scanning 

${DOCKERHUB_CREDS_USR}/${IMAGE_NAME}:b${BUILD_NUMBER} 
  

Example resolved value: 

aayush595/aayush-devsecops:b14 
  

 

2. Severity Filter 

--severity HIGH,CRITICAL 
  

Trivy focuses only on high-risk vulnerabilities. 

This is why your pipeline detects only serious issues. 

 

3. HTML Report Generation 

--format template 
--template @/usr/local/share/trivy/templates/html.tpl 
  

These flags produce a clean, readable HTML report. 

Compatible with: 

Jenkins HTML Publisher Plugin 

Browser preview 

Audit & compliance storage 

 

4. Report Output 

--output trivy-image-report.html 
  

Stored inside Jenkins workspace. 

You can publish it: 

post { 
    always { 
        publishHTML(target: [ 
            allowMissing: true, 
            reportDir: '.', 
            reportFiles: 'trivy-image-report.html', 
            reportName: 'Trivy Image Scan Report' 
        ]) 
    } 
} 
  

(OPTIONAL) 

 

16.6 Why HTML Reports? 

Security teams prefer readable formats 

Managers can download and audit 

Easy to attach in ticketing systems 

Helpful for GitOps approval workflows 

Required during ISO/SOC2 audits 

 

16.7 What This Scan Protects Against 

Log4j critical vulnerabilities 

OpenSSL outdated versions 

Reverse shell backdoors 

Unsafe libraries 

Misconfigured image permissions 

Outdated base image packages 

Hardcoded secrets 

 

16.8 Most Common Issues & Fixes 

Problem 

Cause 

Fix 

“No template file” 

Trivy HTML template missing 

Install template package 

Scan too slow 

Database update each run 

Run: trivy image --skip-db-update 

Permission denied 

Docker not accessible 

Add jenkins to docker group 

No vulnerabilities detected 

Wrong image name 

Verify image exists locally 

 

16.9 Best Practices for Production 

Fail build on critical issues: 

--exit-code 1 
  

Enforce severity level: 

--severity HIGH,CRITICAL 
  

Store SBOM (optional): 

--format cyclonedx --output sbom.xml 
  

Central vulnerability management: 

Upload reports to S3 

Integrate with DefectDojo 

Notify Slack or Teams 

 

This completes the Docker Image Scanning chapter. 

 

CHAPTER 17 — DOCKERHUB PUSH STAGE 

After building and securing your Docker image, the next step is to publish it to a global container registry. 

 Your pipeline uses DockerHub as the image registry. 

This chapter explains: 

What DockerHub is 

Why DevOps uses container registries 

How your pipeline authenticates & pushes images 

How image versioning works 

Why we push only secure images 

Best practices and troubleshooting 

 

17.1 What is DockerHub? 

DockerHub is a public container registry used to store: 

Public Docker images 

Private Docker images 

Versioned container releases 

CI/CD generated images 

It is the default registry used by Docker CLI and Kubernetes. 

 

17.2 Why DevOps Engineers Use Docker Registries 

A container registry provides: 

Central storage for images 

Version management 

Role-based access 

Distribution across environments 

Integration with Kubernetes 

Global accessibility for CI/CD 

Your pipeline pushes images to DockerHub so that: 

ArgoCD can pull them 

Kubernetes can deploy them 

Other environments can reuse them 

 

17.3 Your DockerHub Credentials 

You created Jenkins credential: 

ID: docker 
Username: <DockerHub-username> 
Password: <DockerHub-password> 
  

Used by Jenkinsfile: 

DOCKERHUB_CREDS = credentials('docker') 
  

 

17.4 DockerHub Push Stage in Your Jenkinsfile (Final Version) 

stage('DockerHub Push') { 
    steps { 
        sh ''' 
            echo ${DOCKERHUB_CREDS_PSW} | docker login -u ${DOCKERHUB_CREDS_USR} --password-stdin 
            docker push ${DOCKERHUB_CREDS_USR}/${IMAGE_NAME}:b${BUILD_NUMBER} 
        ''' 
    } 
} 
  

 

17.5 Explanation of the Push Stage 

Step 1 — Logging into DockerHub 

echo ${DOCKERHUB_CREDS_PSW} | docker login -u ${DOCKERHUB_CREDS_USR} --password-stdin 
  

Why we use password-stdin: 

Prevents password exposure in history 

Hides password in Jenkins logs 

More secure than docker login -p 

 

Step 2 — Push the Versioned Image 

docker push ${DOCKERHUB_CREDS_USR}/${IMAGE_NAME}:b${BUILD_NUMBER} 
  

Example resolved value: 

docker push aayush595/aayush-devsecops:b14 
  

This uploads the container image to DockerHub. 

 

17.6 Image Versioning Logic 

Your image tag format: 

b<BUILD_NUMBER> 
  

If Jenkins build number = 14 

 Image = b14 

This gives: 

Unique versions 

Full traceability 

Easy rollback 

Perfect GitOps compatibility 

This is considered a best practice in CI/CD. 

 

17.7 Verify Image in DockerHub 

Visit: 

https://hub.docker.com/repositories 
  

You should see: 

aayush-devsecops 
   ├── b1 
   ├── b2 
   ├── b3 
   └── latest (optional) 
  

 

17.8 Best Practices for DockerHub Push 

Always push scanned images only 

Version images with build numbers, git commit, or semantic tags 

Avoid pushing the latest tag without purpose 

Use private repos for sensitive apps 

Rotate DockerHub tokens periodically 

 

17.9 Common Issues & Fixes 

Problem 

Cause 

Fix 

denied: requested access to the resource is denied 

Wrong username or repo name 

Ensure repo exists on DockerHub 

unauthorized: authentication required 

Incorrect credentials 

Update Jenkins credential 

connection refused 

EC2 blocking outbound 

Enable outbound HTTPS 

too many retries 

Rate limit exceeded 

Use DockerHub PAT (paid tier recommended) 

 

17.10 Integration with GitOps 

After pushing the image: 

Jenkins updates deployment YAML with new image tag 

Commit is pushed to GitOps repo 

ArgoCD detects new commit 

ArgoCD deploys the new image to Kubernetes 

Thus, DockerHub acts as the container source of truth for deployments. 

 

This completes the DockerHub Push Stage. 

 

CHAPTER 18 — UPDATING THE GITOPS REPOSITORY (CD TRIGGER) 

This is one of the most critical chapters in the entire DevSecOps + GitOps workflow. 

Your CI pipeline does NOT deploy to Kubernetes directly. 

Instead: 

Jenkins updates your GitOps Deployment Repository 

ArgoCD continuously watches that repository 

When a change is detected → ArgoCD deploys the update to Kubernetes 

This is the heart of GitOps. 

In this chapter, you will learn: 

What GitOps is 

Why Jenkins updates deployment YAML 

ArgoCD’s pull-based CD 

How your Jenkins stage updates the repo 

Detailed explanation of your GitOps update command 

Folder structure inside CD repo 

 

18.1 What is GitOps? 

GitOps means: 

All Kubernetes manifests are stored and managed in Git, not Jenkins or clusters. 

Git becomes: 

Single source of truth 

Audit history 

Version control 

Deployment trigger 

ArgoCD applies these manifests automatically. 

 

18.2 Why Jenkins Should NOT Apply YAML 

Traditional CI/CD: Jenkins runs: 

kubectl apply -f deployment.yaml 
  

This is NOT GitOps and has problems: 

No audit trail 

No version history 

Hard rollback 

Cluster drift 

Jenkins must have kubeconfig (not recommended) 

With GitOps: 

ArgoCD is the only agent applying YAML 

Jenkins updates only Git repo 

Kubernetes never exposes its credentials to Jenkins 

This is secure and scalable. 

 

18.3 Your GitOps Deployment Repository 

Your CD repo structure: 

Devsecops-aayush-deploy/ 
  ├── base/ 
  │    ├── deployment.yaml 
  │    ├── namespace.yaml 
  │    └── service-nodeport.yaml 
  ├── argocd/ 
  │    └── application.yaml 
  └── kustomization.yaml 
  

The file Jenkins updates: 

Devsecops-aayush-deploy/base/deployment.yaml 
  

Specifically, the image field: 

image: docker.io/aayush595/aayush-devsecops:b13 
  

 

18.4 Your GitOps Update Stage (Final Jenkinsfile Version) 

stage('Update ArgoCD Deployment Repo') { 
    steps { 
        sh ''' 
            rm -rf deploy-repo 
 
            git clone https://${GIT_CREDS_USR}:${GIT_CREDS_PSW}@github.com/Aayushgit18/Devsecops-aayush.git deploy-repo 
 
            cd deploy-repo/Devsecops-aayush-deploy/base 
 
            sed -i "s|image: .*|image: docker.io/${DOCKERHUB_CREDS_USR}/${IMAGE_NAME}:b${BUILD_NUMBER}|" deployment.yaml 
 
            git config --global user.email "jenkins@devops.com" 
            git config --global user.name "Jenkins" 
 
            git add . 
            git commit -m "Updated image to b${BUILD_NUMBER}" 
            git push 
        ''' 
    } 
} 
  

 

18.5 Step-by-Step Explanation 

Step 1 — Cleanup 

rm -rf deploy-repo 
  

Ensures no previous cloned repo remains. 

 

Step 2 — Clone the GitOps Repo 

git clone https://USERNAME:PASSWORD@github.com/... deploy-repo 
  

Uses github-creds stored in Jenkins. 

 

Step 3 — Enter base directory 

cd deploy-repo/Devsecops-aayush-deploy/base 
  

Where your Kubernetes manifests are stored. 

 

Step 4 — Update the image tag 

sed -i "s|image: .*|image: docker.io/<user>/aayush-devsecops:b14|" deployment.yaml 
  

Updates the Deployment manifest with the new image. 

This is the actual CD trigger. 

 

Step 5 — Configure Git identity 

git config --global user.email "jenkins@devops.com" 
git config --global user.name "Jenkins" 
  

Required so Git can commit. 

 

Step 6 — Commit the change 

git add . 
git commit -m "Updated image to b${BUILD_NUMBER}" 
  

Commit log gives a clear audit trail. 

 

Step 7 — Push changes 

git push 
  

Final step. 

Once pushed → ArgoCD detects the commit → Redeploys app automatically. 

 

18.6 GitOps Flow After Update 

Jenkins updates deployment.yaml 
           ↓ 
Commit pushed to GitHub 
           ↓ 
ArgoCD detects change 
           ↓ 
ArgoCD pulls repo 
           ↓ 
ArgoCD syncs Kubernetes manifests 
           ↓ 
New pod (with new image) is created 
  

No “kubectl apply” required. 

 

18.7 Why GitOps is Better 

Traditional CI/CD 

GitOps 

Jenkins → kubectl apply 

Jenkins → Update git 

Cluster credentials in Jenkins 

No cluster credentials exposed 

No version control of manifests 

Full history in Git 

Drift happens 

ArgoCD self-heals 

Rollback difficult 

Git revert → auto rollback 

GitOps is the future of DevOps. 

 

18.8 Verification Commands (on Master Node) 

kubectl get pods -n aayush-app 
kubectl get deployments -n aayush-app 
kubectl describe deployment aayush-devsecops -n aayush-app 
  

You should see: 

Image: docker.io/aayush595/aayush-devsecops:b<BUILD_NUMBER> 
  

 

18.9 Common Problems & Fixes 

Issue 

Cause 

Fix 

Permission denied on git push 

Wrong github-creds 

Update credential 

Image not updated 

sed failed 

Check YAML formatting 

ArgoCD doesn’t deploy 

Auto-sync disabled 

Enable Auto Sync 

Multiple containers 

Wrong selector labels 

Ensure labels match 

 

This completes the GitOps Update Stage. 

 

 

 

CHAPTER 19 — UNDERSTANDING THE COMPLETE JENKINSFILE (FINAL VERSION) 

This chapter combines everything from previous chapters into one unified Jenkins pipeline. 

 You will learn: 

The complete Jenkinsfile (final, production-ready) 

Explanation of each stage 

Why each stage exists 

How credentials and variables are used 

How CI triggers GitOps-based CD 

Why this design is DevSecOps industry standard 

This is the core of your project. 

 

19.1 FULL FINAL JENKINSFILE 

Below is your complete, final, corrected Jenkinsfile exactly as you will use it: 

pipeline { 
    agent any 
 
    environment { 
        // Sonar 
        SONAR_AUTH = credentials('sonar-token') 
        SONAR_URL = credentials('sonar-url') 
 
        // Artifactory 
        ARTIFACTORY_URL = credentials('artifactory-url') 
        ARTIFACTORY_CREDS = credentials('artifactory-creds') 
 
        // DockerHub 
        DOCKERHUB_CREDS = credentials('docker') 
 
        // GitHub (IMPORTANT for GitOps) 
        GIT_CREDS = credentials('github-creds') 
 
        IMAGE_NAME = "aayush-devsecops" 
 
        // Main CI repo 
        DEPLOY_REPO = "https://github.com/Aayushgit18/Devsecops-aayush.git" 
    } 
 
    stages { 
 
        stage('Pull Code') { 
            steps { 
                git branch: 'main', 
                    url: 'https://github.com/Aayushgit18/Devsecops-aayush.git' 
            } 
        } 
 
        stage('Maven Build') { 
            steps { 
                sh ''' 
                    cd java-maven-sonar-argocd-helm-k8s/spring-boot-app 
                    mvn clean package -DskipTests 
                ''' 
            } 
        } 
 
        stage('SonarQube Scan') { 
            steps { 
                sh ''' 
                    cd java-maven-sonar-argocd-helm-k8s/spring-boot-app 
                    mvn sonar:sonar \ 
                      -Dsonar.projectKey=devsecops-aayush \ 
                      -Dsonar.host.url=${SONAR_URL} \ 
                      -Dsonar.token=${SONAR_AUTH} 
                ''' 
            } 
        } 
 
        stage('Trivy FS Scan') { 
            steps { 
                sh ''' 
                    trivy fs java-maven-sonar-argocd-helm-k8s --exit-code 0 --format table 
                ''' 
            } 
        } 
 
        stage('Upload JAR to JFrog Maven Repo') { 
            steps { 
                sh ''' 
                    JAR_FILE=$(find java-maven-sonar-argocd-helm-k8s -name "*.jar" | head -1) 
                    VERSIONED_JAR=spring-boot-web-b${BUILD_NUMBER}.jar 
 
                    cp $JAR_FILE $VERSIONED_JAR 
 
                    curl -u ${ARTIFACTORY_CREDS_USR}:${ARTIFACTORY_CREDS_PSW} \ 
                     -T $VERSIONED_JAR \ 
                     ${ARTIFACTORY_URL}/maven-repo/ 
                ''' 
            } 
        } 
 
        stage('Docker Build') { 
            steps { 
                sh ''' 
                    cd java-maven-sonar-argocd-helm-k8s/spring-boot-app 
                    docker build -t ${DOCKERHUB_CREDS_USR}/${IMAGE_NAME}:b${BUILD_NUMBER} . 
                ''' 
            } 
        } 
 
        stage('Trivy Docker Image Scan (HTML Only)') { 
            steps { 
                sh ''' 
                    trivy image ${DOCKERHUB_CREDS_USR}/${IMAGE_NAME}:b${BUILD_NUMBER} \ 
                    --severity HIGH,CRITICAL \ 
                    --format template \ 
                    --template @/usr/local/share/trivy/templates/html.tpl \ 
                    --output trivy-image-report.html 
                ''' 
            } 
        } 
 
        stage('DockerHub Push') { 
            steps { 
                sh ''' 
                    echo ${DOCKERHUB_CREDS_PSW} | docker login -u ${DOCKERHUB_CREDS_USR} --password-stdin 
                    docker push ${DOCKERHUB_CREDS_USR}/${IMAGE_NAME}:b${BUILD_NUMBER} 
                ''' 
            } 
        } 
 
        stage('Update ArgoCD Deployment Repo') { 
            steps { 
                sh ''' 
                    rm -rf deploy-repo 
 
                    git clone https://${GIT_CREDS_USR}:${GIT_CREDS_PSW}@github.com/Aayushgit18/Devsecops-aayush.git deploy-repo 
 
                    cd deploy-repo/Devsecops-aayush-deploy/base 
 
                    sed -i "s|image: .*|image: docker.io/${DOCKERHUB_CREDS_USR}/${IMAGE_NAME}:b${BUILD_NUMBER}|" deployment.yaml 
 
                    git config --global user.email "jenkins@devops.com" 
                    git config --global user.name "Jenkins" 
 
                    git add . 
                    git commit -m "Updated image to b${BUILD_NUMBER}" 
                    git push 
                ''' 
            } 
        } 
    } 
 
    post { 
        always { 
            echo "Pipeline completed with full DevSecOps + GitOps deployment." 
        } 
    } 
} 
  

 

19.2 Pipeline Stage Breakdown (Stage-by-Stage Explanation) 

1. Pull Code 

Gets CI repository from GitHub. 

 

2. Maven Build 

Compiles Java app and produces JAR file. 

 

3. SonarQube Scan 

Analyzes code quality and security issues. 

 

4. Trivy FS Scan 

Scans filesystem for secrets and vulnerabilities. 

 

5. Upload JAR to Artifactory 

Stores versioned artifact: 

spring-boot-web-b<BUILD_NUMBER>.jar 
  

 

6. Docker Build 

Builds container image using Dockerfile. 

Example tag: 

b14 
  

 

7. Trivy Docker Image Scan 

Scans the built Docker image using HTML report. 

 

8. DockerHub Push 

Publishes secure image to DockerHub. 

 

9. Update ArgoCD Deployment Repo (GitOps Trigger) 

Updates: 

deployment.yaml → new image tag 
  

ArgoCD sees commit → redeploys to Kubernetes. 

 

19.3 Why This Pipeline Is Enterprise-Grade 

Fully automated CI flow 

Secure artifact storage 

Code quality enforcement 

Container security scanning 

Container registry integration 

GitOps-based deployment update 

ArgoCD for automated CD 

End-to-end traceability 

This architecture is used by: 

Netflix 

Amazon 

PayPal 

Zoho 

Walmart 

Many enterprise teams 

 

19.4 What Happens After Pipeline Completes 

New Docker image pushed to DockerHub 

Jenkins updates deployment repo with new image tag 

GitHub commits trigger ArgoCD sync 

ArgoCD deploys new pod in Kubernetes 

App becomes live with new version 

 

19.5 Final CI/CD Flow (Text Diagram) 

Developer Pushes Code 
        ↓ 
      Jenkins (CI) 
 ↓ ↓ ↓ ↓ ↓ ↓ ↓ ↓ ↓ ↓ 
Build → Scan → Secure → Store → Image → Scan → Registry → GitOps Update 
        ↓ 
    GitHub Deployment Repo 
        ↓ 
      ArgoCD (CD) 
        ↓ 
Kubernetes Deploys New Pod Automatically 
  

 

Your final Jenkinsfile is now completely documented. 

 

CHAPTER 20 — INSTALLING KUBERNETES (MASTER NODE SETUP — CONTAINERD) 

This is one of the most important chapters because Kubernetes is the core of your CD environment. 

 This chapter provides the exact, stable, error-free kubeadm installation script for the master node using containerd (not Docker runtime). 

This is the correct and recommended approach for Kubernetes v1.29+. 

 

20.1 Why Kubernetes? 

Kubernetes provides: 

Automated deployment 

Self-healing 

Auto-scaling 

Rolling updates 

Immutable infrastructure 

Container orchestration 

High availability 

Your CI/CD pipeline deploys into Kubernetes via ArgoCD (GitOps). 

 

20.2 Why kubeadm? 

kubeadm is: 

Light 

Stable 

Official Kubernetes installer 

Industry standard 

Easily scripted 

Used by DevOps engineers for labs & production clusters 

 

20.3 Why containerd instead of Docker? 

Kubernetes deprecated Docker runtime 

containerd is official default 

Lighter 

Faster 

Built specifically for Kubernetes 

No need for cri-dockerd 

This eliminates errors like: 

CRI: container runtime is not running 
Error: unable to detect container runtime 
  

 

20.4 Kubernetes Master Node Script (FINAL) 

Create script: 

nano k8s-master-containerd.sh 
  

Paste the complete master script: 

#!/bin/bash 
 
echo "==== STEP 1: Disable swap ====" 
sudo swapoff -a 
sudo sed -i '/ swap / s/^/#/' /etc/fstab 
 
echo "==== STEP 2: Enable required modules ====" 
cat <<EOF | sudo tee /etc/modules-load.d/k8s.conf 
overlay 
br_netfilter 
EOF 
 
sudo modprobe overlay 
sudo modprobe br_netfilter 
 
echo "==== STEP 3: Apply sysctl params ====" 
cat <<EOF | sudo tee /etc/sysctl.d/k8s.conf 
net.bridge.bridge-nf-call-ip6tables = 1 
net.bridge.bridge-nf-call-iptables = 1 
net.ipv4.ip_forward = 1 
EOF 
 
sudo sysctl --system 
 
echo "==== STEP 4: Install containerd ====" 
sudo apt-get update -y 
sudo apt-get install -y ca-certificates curl gnupg lsb-release 
 
sudo mkdir -p /etc/apt/keyrings 
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmour -o /etc/apt/keyrings/docker.gpg 
 
echo \ 
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \ 
  https://download.docker.com/linux/ubuntu \ 
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null 
 
sudo apt-get update -y 
sudo apt-get install -y containerd.io 
 
echo "==== STEP 5: Configure containerd with systemd cgroup ====" 
sudo mkdir -p /etc/containerd 
containerd config default | sudo tee /etc/containerd/config.toml > /dev/null 
 
sudo sed -i 's/SystemdCgroup = false/SystemdCgroup = true/' /etc/containerd/config.toml 
 
sudo systemctl restart containerd 
sudo systemctl enable containerd 
 
echo "==== STEP 6: Install Kubernetes components ====" 
sudo mkdir -p /etc/apt/keyrings 
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.29/deb/Release.key | \ 
  sudo gpg --dearmour -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg 
 
echo "deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] \ 
https://pkgs.k8s.io/core:/stable:/v1.29/deb/ /" | \ 
  sudo tee /etc/apt/sources.list.d/kubernetes.list 
 
sudo apt-get update -y 
sudo apt-get install -y kubelet kubeadm kubectl 
sudo apt-mark hold kubelet kubeadm kubectl 
 
echo "==== STEP 7: kubeadm init (containerd socket) ====" 
sudo kubeadm init \ 
  --cri-socket unix:///run/containerd/containerd.sock \ 
  --pod-network-cidr=192.168.0.0/16 
 
echo "==== STEP 8: Setup kubeconfig ====" 
mkdir -p $HOME/.kube 
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config 
sudo chown $(id -u):$(id -g) $HOME/.kube/config 
 
echo "==== STEP 9: Install Calico CNI ====" 
kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.26.0/manifests/calico.yaml 
 
echo "==== K8S MASTER SETUP COMPLETE ====" 
echo "Run this to get join command: kubeadm token create --print-join-command" 
  

 

20.5 Run the script 

chmod +x k8s-master-containerd.sh 
sudo ./k8s-master-containerd.sh 
  

 

20.6 Output to expect 

You must see: 

Your Kubernetes control-plane has initialized successfully! 
  

Then: 

kubeadm join <MASTER-IP>:6443 --token abcdef.1234567890abcdef \ 
--discovery-token-ca-cert-hash sha256:XXXXXXXX 
  

Save this. 

 This is your worker join command. 

 

20.7 Post-Installation Verification 

Verify Kubernetes cluster is running: 

kubectl get nodes 
kubectl get pods -A 
  

Expected output: 

master   Ready   control-plane 
calico-node running 
kube-dns running 
  

 

20.8 Why Calico CNI? 

Calico provides: 

Pod-to-pod networking 

Network policies 

High performance 

Works well with kubeadm 

Works with GitOps workloads 

 

20.9 Summary of Master Setup 

Component 

Purpose 

Disable swap 

Kubernetes requirement 

containerd 

Runtime engine 

kubelet/kubeadm/kubectl 

Core K8s components 

kubeadm init 

Boots master node 

Calico 

Networking 

Master setup is the foundation of your Kubernetes cluster. 

 

 

 

CHAPTER 21 — INSTALLING KUBERNETES (WORKER NODE SETUP — CONTAINERD) 

Worker nodes run your application workloads (pods). 

 This chapter provides the full worker script identical to industry standards. 

 

21.1 Worker Node Script (Final Version) 

Create script: 

nano k8s-worker-containerd.sh 
  

Paste: 

#!/bin/bash 
 
echo "==== STEP 1: Disable swap ====" 
sudo swapoff -a 
sudo sed -i '/ swap / s/^/#/' /etc/fstab 
 
echo "==== STEP 2: Enable kernel modules ====" 
cat <<EOF | sudo tee /etc/modules-load.d/k8s.conf 
overlay 
br_netfilter 
EOF 
 
sudo modprobe overlay 
sudo modprobe br_netfilter 
 
echo "==== STEP 3: Configure sysctl ====" 
cat <<EOF | sudo tee /etc/sysctl.d/k8s.conf 
net.bridge.bridge-nf-call-ip6tables = 1 
net.bridge.bridge-nf-call-iptables = 1 
net.ipv4.ip_forward = 1 
EOF 
 
sudo sysctl --system 
 
echo "==== STEP 4: Install containerd ====" 
sudo apt-get update -y 
sudo apt-get install -y ca-certificates curl gnupg lsb-release 
 
sudo mkdir -p /etc/apt/keyrings 
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmour -o /etc/apt/keyrings/docker.gpg 
 
echo \ 
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \ 
  https://download.docker.com/linux/ubuntu \ 
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null 
 
sudo apt-get update -y 
sudo apt-get install -y containerd.io 
 
echo "==== STEP 5: Configure containerd ====" 
sudo mkdir -p /etc/containerd 
containerd config default | sudo tee /etc/containerd/config.toml > /dev/null 
 
sudo sed -i 's/SystemdCgroup = false/SystemdCgroup = true/' /etc/containerd/config.toml 
 
sudo systemctl restart containerd 
sudo systemctl enable containerd 
 
echo "==== STEP 6: Install Kubernetes components ====" 
sudo mkdir -p /etc/apt/keyrings 
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.29/deb/Release.key | \ 
  sudo gpg --dearmour -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg 
 
echo "deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] \ 
https://pkgs.k8s.io/core:/stable:/v1.29/deb/ /" | \ 
  sudo tee /etc/apt/sources.list.d/kubernetes.list 
 
sudo apt-get update -y 
sudo apt-get install -y kubelet kubeadm kubectl 
sudo apt-mark hold kubelet kubeadm kubectl 
 
echo "==== WORKER READY TO JOIN ====" 
echo "Run kubeadm join command provided by master" 
  

Run: 

chmod +x k8s-worker-containerd.sh 
sudo ./k8s-worker-containerd.sh 
  

 

21.2 Join Worker to Master 

On master: 

kubeadm token create --print-join-command 
  

Run on worker: 

sudo kubeadm join <MASTER-IP>:6443 --token abcdef... --discovery-token-ca-cert-hash sha256:xxxx 
  

 

21.3 Verify Nodes 

On master: 

kubectl get nodes -o wide 
  

Expected: 

master   Ready 
worker1  Ready 
worker2  Ready 
  

 

CHAPTER 22 — VERIFICATION OF CLUSTER HEALTH 

Commands: 

kubectl get pods -A 
kubectl get nodes 
kubectl describe node <name> 
  

Calico must be running. 

 

CHAPTER 23 — INSTALLING ARGO CD (GITOPS CD ENGINE) 

ArgoCD is your continuous deployment engine. 

 

23.1 What is ArgoCD? 

ArgoCD is a GitOps tool that: 

Watches Git repo 

Detects YAML changes 

Applies them to Kubernetes 

Ensures cluster matches Git state 

Provides UI for deployments 

 

23.2 Install ArgoCD 

kubectl create namespace argocd 
kubectl apply -n argocd \ 
  -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml 
  

 

23.3 Expose ArgoCD via NodePort 

kubectl -n argocd patch svc argocd-server -p ' 
{ 
  "spec": { 
    "type": "NodePort", 
    "ports": [ 
      { 
        "port": 80, 
        "targetPort": 8080, 
        "nodePort": 30007 
      } 
    ] 
  } 
}' 
  

 

23.4 Get password 

kubectl -n argocd get secret argocd-initial-admin-secret \ 
  -o jsonpath="{.data.password}" | base64 --decode 
  

Open: 

http://<MASTER-IP>:30007 
  

Login: 

user: admin 
pass: <decoded> 
  

 

CHAPTER 24 — CREATING ARGO CD APPLICATION 

Apply ArgoCD Application YAML: 

File: argocd/application.yaml 

apiVersion: argoproj.io/v1alpha1 
kind: Application 
metadata: 
  name: aayush-devsecops-app 
  namespace: argocd 
spec: 
  project: default 
  source: 
    repoURL: "https://github.com/Aayushgit18/Devsecops-aayush-deploy.git" 
    targetRevision: main 
    path: . 
  destination: 
    server: https://kubernetes.default.svc 
    namespace: aayush-app 
  syncPolicy: 
    syncOptions: 
      - CreateNamespace=true 
  

Apply: 

kubectl apply -f argocd/application.yaml 
  

ArgoCD UI will show the app. 

 

CHAPTER 25 — GITOPS DEPLOYMENT REPO STRUCTURE 

Your repo: 

Devsecops-aayush-deploy/ 
  ├── base/ 
  │    ├── namespace.yaml 
  │    ├── deployment.yaml 
  │    └── service-nodeport.yaml 
  ├── argocd/ 
  │    └── application.yaml 
  └── kustomization.yaml 
  

 

25.1 namespace.yaml 

apiVersion: v1 
kind: Namespace 
metadata: 
  name: aayush-app 
  

 

25.2 deployment.yaml 

apiVersion: apps/v1 
kind: Deployment 
metadata: 
  name: aayush-devsecops 
  namespace: aayush-app 
spec: 
  replicas: 1 
  strategy: 
    type: Recreate 
  selector: 
    matchLabels: 
      app: aayush-devsecops 
  template: 
    metadata: 
      labels: 
        app: aayush-devsecops 
    spec: 
      containers: 
        - name: aayush-devsecops 
          image: docker.io/aayush595/aayush-devsecops:latest 
          ports: 
            - containerPort: 8080 
  

 

25.3 service-nodeport.yaml 

apiVersion: v1 
kind: Service 
metadata: 
  name: aayush-devsecops-svc 
  namespace: aayush-app 
spec: 
  type: NodePort 
  selector: 
    app: aayush-devsecops 
  ports: 
    - port: 80 
      targetPort: 8080 
      nodePort: 30080 
  

 

25.4 kustomization.yaml 

resources: 
  - base/namespace.yaml 
  - base/deployment.yaml 
  - base/service-nodeport.yaml 
  

 

CHAPTER 26 — ARGO CD SYNC & DEPLOYMENT PROCESS 

Once your GitOps repo is updated: 

ArgoCD detects commit 

ArgoCD syncs YAML 

Kubernetes applies new configuration 

A new pod is created with new image 

Old pod deleted 

You get automated deployment. 

 

CHAPTER 27 — ACCESSING YOUR APPLICATION 

Check pods: 

kubectl get pods -n aayush-app 
  

Check service: 

kubectl get svc -n aayush-app 
  

Access application: 

http://<MASTER-IP>:30080 
  

 

CHAPTER 28 — COMPLETE CI/CD PIPELINE SUMMARY 

CI (Jenkins) 

Pull Code 

Maven Build 

SonarQube Scan 

Trivy FS Scan 

Upload JAR to Artifactory 

Docker Build 

Trivy Image Scan 

Push to DockerHub 

Update GitOps Repo 

 

CD (ArgoCD) 

Watches GitOps repo 

Detect changes 

Sync YAML 

Deploy new pods 

Verify health 

Self-heal if someone changes manually 

 

CHAPTER 29 — WHY THIS PIPELINE IS ENTERPRISE STANDARD 

Full DevSecOps 

GitOps-based CD 

Immutable containers 

Artifact versioning 

Security scanning everywhere 

Kubernetes-native 

Reproducible builds 

Automated deployment 

Used by companies like: 

Netflix 

PayPal 

Amazon 

Walmart 

Spotify 

 

CHAPTER 30 — TROUBLESHOOTING 

Jenkins cannot run docker 

Fix: 

sudo usermod -aG docker jenkins 
  

ArgoCD app stuck OutOfSync 

Fix: Enable auto-sync. 

Pod CrashLoopBackOff 

Fix: Check image tag + logs. 

YAML not updating 

Fix: sed or wrong repo path. 

Trivy slow 

Fix: 

--skip-db-update 
  

 

CHAPTER 31 — FINAL ARCHITECTURE DIAGRAM 

               GitHub (Source Code) 
                        │ 
                        ▼ 
                 Jenkins (CI Engine) 
  ┌──────────────┬───────────────┬───────────────────┐ 
  ▼              ▼               ▼                   ▼ 
Maven       SonarQube       Trivy FS            Artifactory 
Build       Scan            Scan                (JAR Upload) 
                                                
                        │ 
                        ▼ 
                Docker Build → Trivy Image Scan → DockerHub 
                        │ 
                        ▼ 
        Update GitOps Repo (deployment.yaml with new tag) 
                        │ 
                        ▼ 
                ArgoCD (GitOps CD Engine) 
                        │ 
                        ▼ 
               Kubernetes Cluster (Pods/Services) 
  

 

CHAPTER 32 — COMPLETE PROJECT SUMMARY 

You now have a full, end-to-end DevSecOps CI/CD pipeline with: 

Jenkins (CI) 

SonarQube (Code Quality) 

Trivy (Security) 

JFrog Artifactory (Artifacts) 

Docker (Containerization) 

DockerHub (Registry) 

GitHub (Source + GitOps) 

ArgoCD (CD) 

Kubernetes (Deployment) 

This is a production-grade architecture. 

 

 
