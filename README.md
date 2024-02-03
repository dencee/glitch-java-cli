## Overview
To run a Java command-line program as a project on [Glitch](https://glitch.com):
1. Fork this repository.
1. Replace `my_app.jar` with your own jar (named `my_app.jar`, or update `start.sh` with your jar name).
1. On Glitch, select New Project > Import from GitHub, and enter the URL of your GitHub repository.

## How to create my_app.jar (using Maven and the Spring Boot Maven plugin)

* Add this section to your pom.xml file within project/build/plugins, replacing `MyClassWithMainMethod` with the class that contains the main method.
* **Note**: if the class with the main method is in a package, then that must be included as well: `com.example.MyClassWithMainMethod`
```
<build>
    <plugins>
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
            <version>2.4.1</version>
            <configuration>
                <mainClass>
                    MyClassWithMainMethod
                </mainClass>
            </configuration>
        </plugin>
    </plugins>
</build>
```
* Also in the `pom.xml`, make sure the compiler is running java 1.8
```
<properties>
    <maven.compiler.source>1.8</maven.compiler.source>
    <maven.compiler.target>1.8</maven.compiler.target>
</properties>
```
* Build the jar by running in the terminal at the root of the project: `mvn clean package spring-boot:repackage`
* Find the resulting jar in the directory called target, then copy and paste it into the root of the project
* Rename it to `my_app.jar` and confirm it runs with `java -jar my_app.jar`

## IMPORTANT NOTE
Glitch currently only supports Java 8, so make sure your compiler target version is 1.8 in the `pom.xml` as indicated above.
