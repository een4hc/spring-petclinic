#!groovy
pipeline {
  agent none
  environment 
  {
  CI = true
  ARTIFACTORY_ACCESS_TOKEN = credentials('artifactory-access-token')
  }
  stages {
    stage('Maven Install') {
      agent {
        docker {
          image 'maven:3.8.7'
        }
      }
      steps {
        sh 'mvn clean install'
      }
    }
    stage('Docker Build') {
      agent any
      steps {
        sh 'docker build -t een4hc/spring-petclinic:latest .'
      }
    }
    stage('Upload to Artifactory') {
      agent {
        docker {
          image 'releases-docker.jfrog.io/jfrog/jfrog-cli-full-v2-jf jf -v'
          reuseNode true
    }
    }
    steps {
      sh 'jfrog rt upload --url http://localhost:8082/artifactory/ --access-token ${ARTIFACTORY_ACCESS_TOKEN} target/een4hc/spring-petclinic.jar petclinic/'
    }
    
  }    
  }
}
