# Spring-petclinic Pipeline Assignment
The idea behind this assignment is to build a Jenkins Pipeline Project and eventually containerised the application. The image is then Packaged as a runnable Docker image which then gets published the image to JFrog Artifactory


# Steps taken to achieve this:
1. Spring-petclinic is forked to git een4hc/repo spring-petclinic via  (https://github.com/spring-projects/spring-petclinic)
2. Jenkins packaged in docker is downloaded and run on 8080
3. A dockerfile is created on alpine which Runs and resloves Maven dependenicies 
4. A Jenkinsfile is then created that configures pipes. It first looks to declare environment for Jfrog integration such as access token. A latest Maven image is installed and run. A docker image 'een4hc/spring-petclinic' is build.
5. Jenkins is configured with a Pipeline project that connects with een4hc git SCM and Jenkinsfile as the path
6. Local Jfrog artifactory is installed and an access token is generated
7. Jfrog access token is used as Jenkins secret text credentials for authantication 
8. Image is published and pushed to Jfrog artifactory 

