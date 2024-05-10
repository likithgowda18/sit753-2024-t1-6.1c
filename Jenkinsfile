pipeline {
    agent any
    
    stages {
        stage('build') {
            steps {
                    //use a build automation tool like Maven to compile and package the code
                    echo 'Build the code use Maven '
            }
        }
    
    

        stage('Unit and Integration Tests') {
            steps {
                    //use test automation tools like Junit for unit tests and Selenium for integration tests
                    echo 'run unit tests use Junit'
                    echo 'run integration tests use Selenium'
                    echo 'text2'
            }

            post {
                success {
                    emailext to: "likithgowda1802@gmail.com",
                    subject: " Build Status Email",
                    body: "Build was successful",
                    attachLog:true
                }

                failure {
                    emailext to: "likithgowda1802@gmail.com",
                    subject: "Build Status Email",
                    body: "Build was fail",
                    attachLog:true
                }
            }



        }

        stage('Code Analysis') {
            steps {
                    // Intergate a code analysis tool like SonarQube
                    echo 'Analysis integration tests use Selenium'
                
            }
        }

        stage('Security Scan') {
            steps {
                    // Perform security scan use a tool like OWASP ZAP
                    echo 'Performing security scan use OWASP ZAP'
            }

            post {
                success {
                    emailext to: "likithgowda1802@gmail.com",
                    subject: " Build Status Email",
                    body: "Build was successful",
                    attachLog:true
                }
                failure {
                    emailext to: "likithgowda1802@gmail.com",
                    subject: "Build Status Email",
                    body: "Build was fail",
                    attachLog:true
                }
        }
        
    }

        stage('Deploy to staging') {
            steps {
                    // Deploy the application to a staging server like AWS EC2 instance
                    echo 'Deploy the application to staging server'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                    //run integration tests on staging environment
                    echo 'run integration tests on staging environment'
            }
        }

        stage('Deploy to Production') {
            steps {
                    // Deploy the application to a prooduction server like AWS EC2 instance
                    echo 'Deploy the application to production server'
                
            }
        }
    }
    post {
        success {
                mail to: "likithgowda1802@gmail.com",
                subject: "Build Success",
                body: "The build completed successfully."
        }
    }
}

