pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven'
                // Add Maven build commands here
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests using JUnit'
                // Add commands to run unit tests
                
                echo 'Running integration tests using Selenium'
                // Add commands to run integration tests
            }
        }
        
        stage('Code Analysis') {
            steps {
                echo 'Running code analysis using SonarQube'
                // Add commands to run code analysis with SonarQube
            }
        }
        
        stage('Security Scan') {
            steps {
                echo 'Performing security scan using OWASP ZAP'
                // Add commands to perform security scan with OWASP ZAP
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying the application to a staging server (e.g., AWS EC2 instance)'
                // Add commands to deploy to staging
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment'
                // Add commands to run integration tests on staging
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo 'Deploying the application to a production server (e.g., AWS EC2 instance)'
                // Add commands to deploy to production
            }
        }
    }
    
    post {
        always {
            emailext body: 'Pipeline completed: ${currentBuild.result}', subject: 'Pipeline Notification', to: 'likithgowda1802@gmail.com'
        }
    }
}
