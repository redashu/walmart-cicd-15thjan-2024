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

### adding ansible script run in jenkinsfile

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
                    git push https://redashu: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@github.com/redashu/ashu-walmart-releaseb1.git 
                '''
                
            }
        }
        // deploy using ansible 
        stage('ansible based deployment') {
            steps {
                echo 'checking ansible Installation'
                sh 'ansible --version'
                sh 'mkdir /tmp/ashu-ansible'
                dir('/tmp/ashu-ansible') {
                    git branch:'master', url: 'https://github.com/redashu/ashu-walmart-releaseb1.git'
                    echo 'checking ansible details'
                    sh 'ls '
                    // running ansible script 
                    sh 'ansible-playbook -i inventory tomcat.yaml'
                }
                // removing ansible dir 
                sh 'rm -rf /tmp/ashu-ansible/'
            }
        }
    }
    
}

```

### adding ansible deployment 

```
---
- name: Run Date Command on Remote Linux
  hosts: tomcat_server  # Replace with the target host or group of hosts
  remote_user: root 

  tasks:
    - name: Run date command
      command: date
      register: date_output  # Store the output of the date command

    - name: Display date output
      debug:
        var: date_output.stdout

    - name: Clone GitHub repository (specify release)
      git:
        repo: https://github.com/redashu/ashu-walmart-releaseb1.git  # Replace with your GitHub repository URL
        dest: /tmp/deployashu # keep your own name 
        version: release  

    - name: Run ls command to check copied files
      command: cp -v /tmp/deployashu/ashu-webapp.war /opt/apache-tomcat-10.1.18/webapps/
```

### How to setup Email auth with jenkins server details below

<img src="smtp.png">

### jenkinsfile with postbuild action

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
                sh 'mkdir -p /tmp/ashu-ansible'
                dir('/tmp/ashu-ansible') {
                    git branch:'master', url: 'https://github.com/redashu/ashu-walmart-releaseb1.git'
                    echo 'checking ansible details'
                    sh 'ls '
                    // running ansible script 
                    sh 'ansible-playbook -i inventory tomcat.yaml'
                }
                // removing ansible dir 
                
            }
        }
    }
    // define post section 
    post {
        // seccuess section 
        success {
            echo 'okey we got it everything running '
            sh 'rm -rf /tmp/ashu-ansible/'
            // shoot email notification
            mail bcc: 'ishwarmanithapa@gmail.com', body: '''Hey we did it 
all the pipeline with all stages are running successfully''', cc: 'prasadyawalkar1994@gmail.com', from: '', replyTo: '', subject: 'congratulations -- we did it ', to: 'ashutoshhsingh93@gmail.com'
            
        }
        // failure section 
        failure {
            echo 'seems like we got some problem'
        }
        // always 
        always {
            echo 'lets free some cache memory to make performance better'
        }
        
    }
    
}

```
