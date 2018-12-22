#https://www.jianshu.com/p/a25c82bc5260  
#docker run --name mywebapp -p 8080:8080 -d myapp  

#docker build -t myapp .  
#docker images  
#docker run -it #{利用したいイメージ} /bin/bash  
#entered container...  
#java -jar mydockerapp.jar  
#exit  
#lsof -n -i4TCP:8080 | kill -9  

#This is new frontend  
#https://blogg.kantega.no/webapp-with-create-react-app-and-spring-boot/




requirement 1
# Build container image
----------------

## Create a Spring Boot application  

Webapp with Create React App and Spring Boot

- Backend  
 Spring Initializr with web, actuator dependancies
- Frontend   
    with create-react-app
- Database  
    mongoDB




## Packaging a Spring Boot application as a Docker container

```yml 
image: docker:latest
services:
  - docker:dind

#...

docker-build:
  stage: package
  script:
  - docker build -t registry.gitlab.com/satooooshi1/actuator-sample .
  - docker login -u gitlab-ci-token -p $CI_BUILD_TOKEN registry.gitlab.com
  - docker push registry.gitlab.com/satooooshi1/actuator-sample

  #...

  ```

  In gitlab-cli.yml, the docker-build job packages the application into a Docker container.

The scripts are a typical sequence of docker commands used to build an image, log in to a private registry and push the image to it. We will be pushing images to the GitLab Container Registry.

The $CI_BUILD_TOKEN is a pre-defined variable which is injected by GitLab CI into our build environment automatically. It is used to log in to the GitLab Container Registry.

- Used commands  

Build an image from a Dockerfile  
docker build [OPTIONS] PATH | URL | -  
--tag , -t		Name and optionally a tag in the ‘name:tag’ format  
. at the end means build at current directory  

Log in to a Docker registry
docker login [OPTIONS] [SERVER]  
--password , -p		Password  
--password-stdin		Take the password from stdin  
--username , -u		Username  

Push an image or a repository to a registry
docker push [OPTIONS] NAME[:TAG]




## creating the Dockerfile in the root directory of our project.
 *Docker can build images automatically by reading the instructions from a Dockerfile . A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image.*
```Dockerfile
FROM openjdk:8u111-jdk-alpine
VOLUME /tmp
ADD ./build/libs/actuator-sample-0.0.1-SNAPSHOT.jar app.jar
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]
```  


The FROM keyword defines the base Docker image of our container. We chose OpenJDK installed on Alpine Linux which is a lightweight Linux distribution. The VOLUME instruction creates a mount point with the specified name and marks it as holding externally mounted volumes from the native host or other containers. ADD copies the executable JAR generated during the build to the container root directory. Finally ENTRYPOINT defines the command to execute when the container is started. Since Spring Boot produces an executable JAR with embedded Tomcat, the command to execute is simply java -jar app.jar. The additiona flag java.security.edg=file:/dev/./urandom is used to speed up the application start-up and avoid possible freezes. By default, Java uses /dev/random to seed its SecureRandom class which is known to block if its entropy pool is empty.



## Reference
1. [Continuous delivery of a Spring Boot application with GitLab CI and Kubernetes](https://blogg.kantega.no/webapp-with-create-react-app-and-spring-boot/) 

2. [Webapp with Create React App and Spring Boot](https://about.gitlab.com/2016/12/14/continuous-delivery-of-a-spring-boot-application-with-gitlab-ci-and-kubernetes/)