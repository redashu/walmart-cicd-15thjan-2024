# walmart-cicd-15thjan-2024

### SCM and VSC type 

<img src="scm1.png">

### accessing lab from local laptop using vscode 

<img src="lab.png">

### testing lab access from mac 

```
 ~ ssh  ashu@34.202.73.46 
The authenticity of host '34.202.73.46 (34.202.73.46)' can't be established.
ED25519 key fingerprint is SHA256:kueyu2+SHir6DIn0nHT8+M73FbqB6/LPkzhC/+g9szU.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '34.202.73.46' (ED25519) to the list of known hosts.
ashu@34.202.73.46's password: 
   ,     #_
   ~\_  ####_        Amazon Linux 2
  ~~  \_#####\
  ~~     \###|       AL2 End of Life is 2025-06-30.
  ~~       \#/ ___
   ~~       V~' '->
    ~~~         /    A newer version of Amazon Linux is available!
      ~~._.   _/
         _/ _/       Amazon Linux 2023, GA and supported until 2028-03-15.
       _/m/'           https://aws.amazon.com/linux/amazon-linux-2023/

-bash: warning: setlocale: LC_CTYPE: cannot change locale (UTF-8): No such file or directory
[ashu@git-linux-server ~]$ 
[ashu@git-linux-server ~]$ 
[ashu@git-linux-server ~]$ 
[ashu@git-linux-server ~]$ whoami
ashu
[ashu@git-linux-server ~]$ 


```

### same way using windows laptop also but using powershell

### Installing git in linux server

<img src="git.png">

### installation link

[click_here](https://www.git-scm.com/downloads)

### Installing git on linux (redhat)

```
[ec2-user@ip-172-31-29-249 ~]$ sudo yum install git -y
Failed to set locale, defaulting to C
Loaded plugins: extras_suggestions, langpacks, priorities, update-motd
amzn2-core                                                                                                                            | 3.6 kB  00:00:00     
Resolving Dependencies
--> Running transaction check
---> Package git.x86_64 0:2.40.1-1.amzn2.0.1 will be installed
--> Processing Dependency: git-core = 2.40.1-1.amzn2.0.1 for package: git-2.40.1-1.amzn2.0.1.x86_64
--> Processing Dependency: git-core-doc = 2.40.1-1.amzn2.0.1 for package: git-2.40.1-1.amzn2.0.1.x86_64
--> Processing Dependency: perl-Git = 2.40.1-1.amzn2.0.1 for package: git-2.40.1-1.amzn2.0.1.x86_64
--> Processing Dependency: perl(Git) for package: git-2.40.1-1.amzn2.0.1.x86_64
--> Processing Dependency: perl(Term::ReadKey) for package: git-2.40.1-1.amzn2.0.1.x86_64
--> Running transaction check

```


### verify 

```
[ashu@git-linux-server ~]$ git version 
git version 2.40.1
[ashu@git-linux-server ~]$ 

```

