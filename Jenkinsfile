pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building Java projects with Maven'
                echo '-->mvn clean package'
            }
        }
        
        stage('Unit and Integration Tests') {
            steps 
            {
                echo 'Run JUnit unit tests'
                echo '-->mvn test'
                echo 'Run Selenium integration test'
                echo '-->run_selenium_tests.bat'
            }
            post 
            {
                failure 
                {
                mail to: 'reanyphasy@gmail.com',
                subject: 'The stage construction of Unit and Integration Tests failed.',
                body: 'Unit and Integration Tests failed, please check the log for details.',
                attachLog: true
                }
                success 
                {
                mail to: 'reanyphasy@gmail.com',
                subject: 'The stage construction of unit and integration tests succeeded.',
                body: 'Unit and Integration Tests succeeded',
                attachLog: true
                }
            }
        }
        
        stage('Code Analysis') {
            steps {
                echo 'Integrating SonarQube for code analysis'
                echo '-->sonar-scanner'
            }
        }
        
        stage('Security Scan') {
            steps {
                echo 'Use OWASP ZAP for security scanning'
                echo'--owasp-zap-scan'
            }
             post 
            {
                failure 
                {
                mail to: 'reanyphasy@gmail.com',
                subject: 'The stage construction of Security Scan failed.',
                body: 'Security Scan failed, please check the log for details.',
                attachLog: true
                }
                success 
                {
                mail to: 'reanyphasy@gmail.com',
                subject: 'The stage construction of Security Scan succeeded.',
                body: 'Security Scan succeeded',
                attachLog: true
                }
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying EC2 instance of Staging using AWS CloudFormation'
                echo '-->Deploying the application to a staging server......'
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests in Staging environment'
                echo '-->Running.........'
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo 'Deploying EC2 instance of Staging using AWS CloudFormation'
                echo '-->Deploying the application to a production server........'
            }
        }
    }
    
    
}
