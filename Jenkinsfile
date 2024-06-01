pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                sh 'mvn test'
            }
            post {
                success {
                    script {
                        def logFile = 'unit_test.log'
                        sh "mvn test | tee ${logFile}"
                        emailext (
                            to: 'likithgowda1802@gmail.com',
                            subject: "Build Success - Unit and Integration Tests",
                            body: "The Unit and Integration Tests completed successfully.",
                            attachLog: true,
                            attachmentsPattern: logFile
                        )
                    }
                }
                failure {
                    script {
                        def logFile = 'unit_test.log'
                        sh "mvn test | tee ${logFile}"
                        emailext (
                            to: 'likithgowda1802@gmail.com',
                            subject: "Build Failure - Unit and Integration Tests",
                            body: "The Unit and Integration Tests failed.",
                            attachLog: true,
                            attachmentsPattern: logFile
                        )
                    }
                }
            }
        }

        stage('Code Analysis') {
            steps {
                sh 'mvn checkstyle:check'
            }
        }

        stage('Security Scan') {
            steps {
                sh 'snyk test'
            }
            post {
                success {
                    script {
                        def logFile = 'security_scan.log'
                        sh "snyk test | tee ${logFile}"
                        emailext (
                            to: 'likithgowda1802@gmail.com',
                            subject: "Build Success - Security Scan",
                            body: "The Security Scan completed successfully.",
                            attachLog: true,
                            attachmentsPattern: logFile
                        )
                    }
                }
                failure {
                    script {
                        def logFile = 'security_scan.log'
                        sh "snyk test | tee ${logFile}"
                        emailext (
                            to: 'likithgowda1802@gmail.com',
                            subject: "Build Failure - Security Scan",
                            body: "The Security Scan failed.",
                            attachLog: true,
                            attachmentsPattern: logFile
                        )
                    }
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'deploying'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                sh 'mvn integration-test'
            }
        }

        stage('Deploy to Production') {
            steps {
                sh 'mvn deploy -P production'
            }
        }
    }

    post {
        success {
            emailext (
                to: 'likithgowda1802@gmail.com',
                subject: "Build Success",
                body: "The build completed successfully.",
                attachLog: true
            )
        }
        failure {
            emailext (
                to: 'likithgowda1802@gmail.com',
                subject: "Build Failure",
                body: "The build failed.",
                attachLog: true
            )
        }
    }
}
