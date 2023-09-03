pipeline
 {
    agent any
    
    stages 
    {
        stage("Build")
         {
            steps {
                echo "Building Java projects with Maven"
                echo "-->mvn clean package"
             echo "buildbuildbuild..."
            }
        }
        
        stage("Unit and Integration Tests")
         {
            steps 
            {
                echo "Run JUnit unit tests"
                echo "-->mvn test"
                echo "Run Selenium integration test"
                echo "-->run seleniumtests"
                
            }
            post 
            {
                success 
                {
                 emailext to:"reanyphasy@gmail.com",
                 attachLog:true,
                 subject:"The stage construction of unit and integration tests succeeded",
                 body:"Unit and Integration Tests succeeded!"
                
                }
                failure 
                {
                    emailext to: "reanyphasy@gmail.com",
                    attachLog:true,
                    subject: "The stage construction of Unit and Integration Tests failed",
                     body: "Unit and Integration Tests failed, please check the log for details."
                
                }
                
            }
        }
        
        stage("Code Analysis")
         {
            steps {
                echo "Integrating SonarQube for code analysis"
                echo "-->sonar-scanner"
            }
        }
        
        stage("Security Scan") 
        {
            steps
             {
                echo "Use OWASP ZAP for security scanning"
                echo"--owasp-zap-scan"
            }
             post 
            {
                success 
                {
                    emailext to: 'reanyphasy@gmail.com',
                    subject: "The stage construction of Security Scan succeeded",
                       attachLog:true,
                        body: "Security Scan succeeded !"
                      
                }
                failure 
                {
                emailext to: "reanyphasy@gmail.com",
                attachLog:true,
                subject: "The stage construction of Security Scan failed",
                body: "Security Scan failed, please check the log for details."
                
                }
                
            }
        }
        
        stage("Deploy to Staging")
         {
            steps {
                echo "Deploying EC2 instance of Staging using AWS CloudFormation"
                echo "-->Deploying the application to a staging server......"
            }
        }
        
        stage("Integration Tests on Staging") 
        {
            steps {
                echo "Running integration tests in Staging environment"
                echo "-->Running........."
            }
        }
        
        stage("Deploy to Production")
         {
            steps {
                echo "Deploying EC2 instance of Staging using AWS CloudFormation"
                echo "-->Deploying the application to a production server........"
            }
        }
    }
    
    
}
