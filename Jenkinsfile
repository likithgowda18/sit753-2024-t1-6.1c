pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'mvn clean'
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo 'mvn test'
            }
            post {
                success {
                    emailext(
                        to: "likithgowda1802@gmail.com",
                        subject: "Unit and Integration Test Stage: Success",
                        body: "The Unit and Integration Test stage was successful.",
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: "likithgowda1802@gmail.com",
                        subject: "Unit and Integration Test Stage: Failure",
                        body: "The Unit and Integration Test stage failed.",
                        attachLog: true
                    )
                }
            }
        }
        
        stage('Code Analysis') {
            steps {
                echo 'mvn checkstyle:check'
            }
        }
        
        stage('Security Scan') {
            steps {
                echo 'snyk test'
            }
            post {
                success {
                    emailext(
                        to: "likithgowda1802@gmail.com",
                        subject: "Security Scan Stage: Success",
                        body: "The Security Scan stage was successful.",
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: "likithgowda1802@gmail.com",
                        subject: "Security Scan Stage: Failure",
                        body: "The Security Scan stage failed.",
                        attachLog: true
                    )
                }
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging server'
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo 'mvn integration-test'
            }
            post {
                success {
                    emailext(
                        to: "likithgowda1802@gmail.com",
                        subject: "Integration Tests on Staging Stage: Success",
                        body: "The Integration Tests on Staging stage was successful.",
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: "likithgowda1802@gmail.com",
                        subject: "Integration Tests on Staging Stage: Failure",
                        body: "The Integration Tests on Staging stage failed.",
                        attachLog: true
                    )
                }
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo 'mvn production'
            }
        }
    }
    
    post {
        success {
            emailext(
                to: "likithgowda1802@gmail.com",
                subject: "Build Success",
                body: "The build completed successfully.",
                attachLog: true
            )
        }
        failure {
            emailext(
                to: "likithgowda1802@gmail.com",
                subject: "Build Failure",
                body: "The build failed.",
                attachLog: true
            )
        }
    }
}
