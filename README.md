Description
============

This project works as remote repository to include jars into your project.

Contribution
=============

In order to add jars to this remote repository do the following - In the example given below, we like to add the Jar for REST Testing Helper to this repository.
The groupId refers to the groupId you have specified in your pom.xml The artifactId refers to the artifactId you have specified in your pom.xml The file parameter points to the location where the jar file exists for your new project The localRepositoryPath points to the local repository folder. 

0- Clone the project (git clone https://github.com/alirezafallahi/mvn-repo.git) in your home/IdeaProjects directory. 

1- Cd to the location of your artifact-to-be. (e.g. IdeaProjects/db-connector/target)

2- At terminal do:
 
$ mvn deploy:deploy-file -DgroupId=com.inosol -DartifactId=db-connector -Dversion=1.0-SNAPSHOT -Dpackaging=jar -Dfile="db-connector-1.0-SNAPSHOT.jar" -Durl=file:/home/alirezafallahi/IdeaProjects/mvn-repo/releases

3- Change directory back to the mvn-repo directory created from step 0 and do below:
  
$ git add .
$ git commit -m "new commit"
$ git push origin master

Usage
======

Lets imagine that you have created a new maven project called 'Test' and you like to incorporate the db-connector jar in this project. 
You can simply do this by adding the below configuration details to your pom.xml file.

<dependencies>
	<dependency>
            <groupId>com.inosol</groupId>
            <artifactId>db-connector</artifactId>
            <version>1.0-SNAPSHOT</version>
        </dependency>
</dependencies>


After the build tag add this:

<repositories>
        <repository>
            <id>alirezafallahi-releases</id>
            <releases>
                <enabled>true</enabled>
                <updatePolicy>always</updatePolicy>
                <checksumPolicy>fail</checksumPolicy>
            </releases>
            <url>https://raw.github.com/alirezafallahi/mvn-repo/master/releases</url>
        </repository>
</repositories>
