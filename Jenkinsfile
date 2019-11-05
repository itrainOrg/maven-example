pipeline {
    agent any 
    stages {
        stage('Code Checkout') { 
            steps {
                sh 'echo code checkout'
                git credentialsId: 'githubID', url: 'https://github.com/itrainpulsars/maven-example.git'
            }
        }
        stage('Build') { 
            steps {
              withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
               sh 'mvn clean compile'
             } 
            }
        }
        stage('Test') { 
            steps {
               withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
               sh 'mvn test'
             }  
            }
        }
        stage('code ananlysis') { 
            steps {
                withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
               sh 'mvn  sonar:sonar \
  -Dsonar.projectKey=maven-exam \
  -Dsonar.organization=itrain \
  -Dsonar.host.url=https://sonarcloud.io \
  -Dsonar.login=87c01abc4c9eae3bf0df7d1f14434910ec45e8fc
             }  
            }
        }
        
        stage('Package') { 
            steps {
                withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
               sh 'mvn package'
             }  
            }
        }
        stage('Docker Image') { 
            steps {
                sh 'echo Docker Image' 
            }
        }
        stage('Deploy to Dev') { 
            steps {
                sh 'echo Deploy to Dev' 
            }
        }
        stage('Deploy to Prod') { 
            steps {
                sh 'echo Deploy to Prod' 
            }
        }
    }
}
