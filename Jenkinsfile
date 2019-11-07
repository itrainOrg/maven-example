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
        stage('code Analysis') { 
            steps {
                withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
               sh 'mvn  sonar:sonar \
                     -Dsonar.projectKey=maven-project-example \
                     -Dsonar.organization=itrain-project \
                     -Dsonar.host.url=https://sonarcloud.io \
                     -Dsonar.login=84ac824349ac2903d832226f0bd2d0db96f04964'
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
