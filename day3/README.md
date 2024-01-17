# walmart-cicd-15thjan-2024

### Creating webapp using maven from vscode 

```
ashu@git-linux-server java-app]$ ls
ashu2-demo  ashudemo  ashu-webapp
[ashu@git-linux-server java-app]$ tree  ashu-webapp/
ashu-webapp/
├── pom.xml
└── src
    └── main
        └── webapp
            ├── index.jsp
            └── WEB-INF
                └── web.xml

4 directories, 3 files
```

### doing mvn install 

```
[ashu@git-linux-server ashu-webapp]$ mvn install 
[INFO] Scanning for projects...
[INFO] 
[INFO] ---------------------< com.ashutoshh:ashu-webapp >----------------------
[INFO] Building ashu-webapp Maven Webapp 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ war ]---------------------------------
[INFO] 
[INFO] --- resources:3.0.2:resources (default-resources) @ ashu-webapp ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory /home/ashu/ashu-projects/java-app/ashu-webapp/src/main/resources
[INFO] 
[INFO] --- compiler:3.8.0:compile (default-compile) @ ashu-webapp ---
[INFO] No sources to compile
[INFO] 
[INFO] --- resources:3.0.2:testResources (default-testResources) @ ashu-webapp ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory /home/ashu/ashu-projects/java-app/ashu-webapp/src/test/resources
[INFO] 
[INFO] --- compiler:3.8.0:testCompile (default-testCompile) @ ashu-webapp ---
[INFO] No sources to compile
[INFO] 
[INFO] --- surefire:2.22.1:test (default-test) @ ashu-webapp ---
[INFO] No tests to run.
[INFO] 
[INFO] --- war:3.2.2:war (default-war) @ ashu-webapp ---
[INFO] Packaging webapp
[INFO] Assembling webapp [ashu-webapp] in [/home/ashu/ashu-projects/java-app/ashu-webapp/target/ashu-webapp]
[INFO] Processing war project
[INFO] Copying webapp resources [/home/ashu/ashu-projects/java-app/ashu-webapp/src/main/webapp]
[INFO] Webapp assembled in [18 msecs]
[INFO] Building war: /home/ashu/ashu-projects/java-app/ashu-webapp/target/ashu-webapp.war
[INFO] 
[INFO] --- install:2.5.2:install (default-install) @ ashu-webapp ---
[INFO] Installing /home/ashu/ashu-projects/java-app/ashu-webapp/target/ashu-webapp.war to /home/ashu/.m2/repository/com/ashutoshh/ashu-webapp/1.0-SNAPSHOT/ashu-webapp-1.0-SNAPSHOT.war
[INFO] Installing /home/ashu/ashu-projects/java-app/ashu-webapp/pom.xml to /home/ashu/.m2/repository/com/ashutoshh/ashu-webapp/1.0-SNAPSHOT/ashu-webapp-1.0-SNAPSHOT.pom
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  1.414 s
[INFO] Finished at: 2024-01-17T08:53:12Z
[INFO] ------------------------------------------------------------------------



[ashu@git-linux-server ashu-webapp]$ ls
pom.xml  src  target
[ashu@git-linux-server ashu-webapp]$ ls target/
ashu-webapp  ashu-webapp.war  maven-archiver
```

### incase you are only testing install then want to remove -- target outcome 

```
 mvn clean 
[INFO] Scanning for projects...
[INFO] 
[INFO] ---------------------< com.ashutoshh:ashu-webapp >----------------------
[INFO] Building ashu-webapp Maven Webapp 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ war ]---------------------------------
Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-clean-plugin/3.1.0/maven-clean-plugin-3.1.0.pom
Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-clean-plugin/3.1.0/maven-clean-plugin-3.1.0.pom (5.2 kB at 25 kB/s)
Downloading from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-clean-plugin/3.1.0/maven-clean-plugin-3.1.0.jar
Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/maven/plugins/maven-clean-plugin/3.1.0/maven-clean-plugin-3.1.0.jar (30 kB at 1.6 MB/s)
[INFO] 
[INFO] --- clean:3.1.0:clean (default-clean) @ ashu-webapp ---
[INFO] Deleting /home/ashu/ashu-projects/java-app/ashu-webapp/target
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.839 s
[INFO] Finished at: 2024-01-17T08:54:19Z
```

### additional commands

```
 mvn clean 
  235  ls
  236  mvn install
  237  ls
  238  mvn package
  239  ls
  240  history 
  241  mvn compile
  242  mvn test
```

### Testing war file on apache tomcat

<img src="tomcat.png">

