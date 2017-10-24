#!/usr/bin/env groovy

node {
    docker.image('maven:3-alpine').withRun('-v /root/.m2:/root/.m2).inside {
            
      stage('Build') {
        checkout scm
        sh 'mvn -B -DskipTests clean package'
      }
      
      stage('Test') {
        sh 'mvn test'
      }
      
      stage('Deliver') 
        sh './jenkins/scripts/deliver.sh'
      }
    }
}
