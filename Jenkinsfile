#!/usr/bin/env groovy

node {
    docker.image('maven:3-alpine').inside(' -v /home/jenkins/.m2:/root/.m2') {
            
      stage('Build') {
        checkout scm
        sh 'mvn -B -DskipTests -e -X clean package'
      }
      
      stage('Test') {
        sh 'mvn test'
      }
      
      stage('Deliver') {
        sh './jenkins/scripts/deliver.sh'
      }
    }
}
