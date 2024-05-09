
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Use Maven or any build tool to compile and package your code"
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo "Use test automation tools for unit and integration tests (e.g., JUnit)"
            }
            post {
                success {
                    emailext(
                        to: "likithgowda1802@gmail.com",
                        subject: "Unit and Integration Test Stage: Success",
                        body: "Unit and Integration Test Stage was successful.",
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: "likithgowda1802@gmail.com",
                        subject: "Unit and Integration Test Stage: Failure",
                        body: "Unit and Integration Test Stage failed.",
                        attachLog: true
                    )
                }
        }
        }

        stage('Code Analysis') {
            steps {
                echo "Integrate a code analysis tool (e.g., SonarQube) to analyze the code"
            }
        }

        stage('Security Scan') {
            steps {
                echo "Integrate a security scanning tool (e.g., OWASP ZAP) to scan the code"
            }
            post {
                success {
                    emailext(
                        to: "likithgowda1802@gmail.com",
                        subject: "Security Scan Stage: Success",
                        body: "The security scan stage was successful.",
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: "likithgowda1802@gmail.com",
                        subject: "Security Scan Stage: Failure",
                        body: "The security scan stage failed.",
                        attachLog: true
                    )
                }
        }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Deploy to a staging server (e.g., AWS EC2)"
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "Run integration tests on the staging environment (e.g., Selenium WebDriver)"
            }
            post {
                success {
                    emailext(
                        to: "likithgowda1802@gmail.com",
                        subject: "Integration Tests on Staging Stage: Success",
                        body: "Integration Tests on Staging stage was successful.",
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: "likithgowda1802@gmail.com",
                        subject: "Integration Tests on Staging Stage: Failure",
                        body: "Integration Tests on Staging Stage failed.",
                        attachLog: true
                    )
                }
        }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploy to a production server.. (e.g., AWS EC2)"
            }
        }
    }
}
