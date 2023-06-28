pipeline {
    agent any 
    environment {
        DOCKERHUB_USERNAME = "prvinsm21"
    }
    stages {
        stage ('Git Checkout') {
            steps {
                sh 'echo Passed'
            }
        }
        stage ('Build and Test') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage ('Static Code Analysis') {
            steps {
                script {
                    withSonarQubeEnv(credentialsId: 'sonar-api') {
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
    }
}