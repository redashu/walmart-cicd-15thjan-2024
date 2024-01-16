### Revision 

<img src="rev.png">

### Git hub repo clone and authentication understanding 

<img src="clone1.png">


### https clone -- demo  and push 

```
 cd  /tmp 
➜  /tmp git clone https://github.com/redashu/ashu-mavenops.git
Cloning into 'ashu-mavenops'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
➜  /tmp cd  ashu-mavenops


➜  ashu-mavenops git:(master) ls
README.md
➜  ashu-mavenops git:(master) echo hello >hello.java
➜  ashu-mavenops git:(master) ✗ ls
README.md  hello.java


➜  ashu-mavenops git:(master) ✗ git add .
➜  ashu-mavenops git:(master) ✗ git commit -m "hello java auth test"
[master 358a472] hello java auth test
 1 file changed, 1 insertion(+)
 create mode 100644 hello.java

====>> using username and password -- it will fail as per new github policy

➜  ashu-mavenops git:(master) git push 
Username for 'https://github.com': redashu
Password for 'https://redashu@github.com': 
remote: Support for password authentication was removed on August 13, 2021.
remote: Please see https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls for information on currently recommended modes of authentication.
fatal: Authentication failed for 'https://github.com/redashu/ashu-mavenops.git/'

====>> now using git personal access token 
➜  ashu-mavenops git:(master) git push 
Username for 'https://github.com': redashu
Password for 'https://redashu@github.com': 
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 286 bytes | 286.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/redashu/ashu-mavenops.git
   37b7613..358a472  master -> master

```
