pipeline {
    agent any
    
    tools {
        jdk 'JDK21'
        maven 'Maven'
    }

    stages {
        stage('Hello') {
            steps {
                echo 'Pipeline started!'
                echo "Build number: ${env.BUILD_NUMBER}"
                echo "Building on: ${env.NODE_NAME}"
            }
        }
        
        stage('Checkout') {
            steps {
                echo 'Code checked out from Git'
            }
        }
        
        stage('Build') {
            steps {
                dir('starter_code') {
                    sh 'mvn clean compile'
                }
            }
        }
        
        stage('Test') {
            steps {
                dir('starter_code') {
                    sh 'mvn test'
                }
            }
        }
        
        stage('Package') {
            steps {
                dir('starter_code') {
                    sh 'mvn package -DskipTests'
                }
            }
        }
    }
    
    post {
        success {
            echo '✅ Pipeline completed successfully!'
            echo "Artifact: target/*.jar"
        }
        failure {
            echo '❌ Pipeline failed! Check the logs above for errors.'
        }
        always {
            echo 'Pipeline finished.'
        }
    }
}
