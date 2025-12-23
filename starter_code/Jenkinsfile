pipeline {
    agent any
    
    tools {
        jdk 'JDK21'
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
                git branch: 'main', url: 'https://github.com/251027-Java/jenkins-pipeline-walkerrd2.git'
            }
        }
        
        stage('Build') {
            steps {
                dir('starter_code') {
                    sh 'chmod +x mvnw'
                    sh './mvnw clean compile'
                }
            }
        }
        
        stage('Test') {
            steps {
                dir('starter_code') {
                    sh './mvnw test'
                }
            }
        }
        
        stage('Package') {
            steps {
                dir('starter_code') {
                    sh './mvnw package -DskipTests'
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
