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
