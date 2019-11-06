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
               sh 'mvn sonar:sonar \
               -Dsonar.projectKey=itrain \
               -Dsonar.organization=itrain \
               -Dsonar.host.url=https://sonarcloud.io \
               -Dsonar.login=944aac10bb8b1fc1cd5d6192a6733c2ef1ecbb33
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
