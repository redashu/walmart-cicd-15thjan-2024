# walmart-cicd-15thjan-2024

### Revision of cicd -- Delivery and deployment 

<img src="dd.png">

### exploring more continious deployment 

<img src="cd.png">

### CD in more details 

<img src="ansible.png">

### jenkinsfile with ansible check

```
pipeline {
    agent any

    stages {
        // this is first stage or you can say first job with given steps
        stage('taking source code from git repo ') {
            steps {
                echo 'Hello World'
                sh 'whoami'
                // using git plugin to clone repo 
                git branch: 'master', url: 'https://github.com/redashu/ashu-mvnweb-project.git'
                sh 'ls -a'
            }
        }
        // addin SAST in source 
        stage('doing security check in source code') {
            steps {
                echo 'starting with code checking process'
                
            }
        }
        // building above repo code using maven 
        stage('mvn build stage') {
            steps {
                echo 'building war file using mvn '
                 // build project
                sh '/opt/maven39/bin/mvn  install'
                sh 'ls target'
                sh 'mkdir -p /tmp/ashunew/'
                sh 'cp -rf target/*.war /tmp/ashunew/'
                sh '/opt/maven39/bin/mvn clean'
            }
        }
        // push war file to new git repo in release branch 
        
        stage('pushing code') {
            steps {
                echo 'pushing only war file to new repo '
                sh 'mkdir -p pushdata'
                dir('pushdata') {
                    git 'https://github.com/redashu/ashu-walmart-releaseb1.git'
                }
                
                sh 'ls -a'
                
                sh '''
                    cd pushdata
                    git checkout release
                    cp -rf /tmp/ashunew/*.war .
                    git add .
                    git commit -m "hello war update"
                    git push https://redashu:password@github.com/redashu/ashu-walmart-releaseb1.git 
                '''
                
            }
        }
        // deploy using ansible 
        stage('ansible based deployment') {
            steps {
                echo 'checking ansible Installation'
                sh 'ansible --version'
            }
        }
    }
    
}

```
