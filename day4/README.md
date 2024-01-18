# walmart-cicd-15thjan-2024

### REVision 

<img src="rev.png">

### understanding pipeline jobs  

<img src="pipeline.png">

### job 1 -- build steps 

```
echo "fetching maven based webapp code from GIThub "
echo "checking content as given below"
ls
### checking mvn version 
source ~/.bashrc # loading path without restart jenkins service
mvn --version 
# doing maven install
mvn install 
sleep 2
ls  target
# copy war file to somewhere
mkdir -p /tmp/ashu/
cp -rf target/*.war   /tmp/ashu/
# clean the build 
mvn clean 
```


### Creating job 2 -- build step 

```
ls -a
git branch -a
# change branch 
git checkout release
cp -rf /tmp/ashu/*.war  . 
# update 
git add .
git commit -m "updating war file to new git repo "
git push https://redashu:pasword@github.com/redashu/ashu-walmart-releaseb1.git 

```
## Introduction to scripting  method of jenkinsfile for creating pipeline jobs 

<img src="pipe2.png">

### understanding pipeline jobs 

<img src="jfile.png">

### Example 1 of jenkinsfile 

```
pipeline {
    agent any

    stages {
        // this is first stage or you can say first job with given steps
        stage('test what we get') {
            steps {
                echo 'Hello World'
                sh 'whoami'
                sh 'ls -a'
            }
        }
    }
}

```

### jenkinsfile updated

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
                git 'https://github.com/redashu/ashu-mvnweb-project.git'
                sh 'ls -a'
                // build project
                sh '/opt/maven39/bin/mvn  install'
                sh 'ls target'
            }
        }
    }
}

```
