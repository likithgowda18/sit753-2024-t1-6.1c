
pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'sh \'mvn clean\''
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo 'sh \'mvn test\''
            }
            post {
        success {
           
                mail to: "purvasha1013@gmail.com",
                subject: "Build Success",
                body: "The Unit and Integration Test is successfull."     
        }
    }
        }
        
        stage('Code Analysis') {
            steps {
                echo 'sh \'mvn checkstyle:check\''
            }
        }
        
        stage('Security Scan') {
            steps {
                echo 'sh \'snyk test\''
            }
            post {
        success {
           
                mail to: "purvasha1013@gmail.com",
                subject: "Build Success",
                body: "The Security Scan check is completed successfully."     
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
                echo 'sh \'mvn integration-test\''
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
           
                mail to: "purvasha1013@gmail.com",
                subject: "Build Success",
                body: "The build completed successfully."
                
        }
    }
}
