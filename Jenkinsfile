pipeline {
    agent any

    environment
     {
        DIRECTORY_PATH = "D:\\jenkinss"
        TESTING_ENVIRONMENT = "testing-environment"
        PRODUCTION_ENVIRONMENT = "Leyan Chen's production-environment"
    }

    stages {
        stage('Build') 
        {
            steps 
            {
                bat "echo Fetch the source code from the directory path: $DIRECTORY_PATH"
                echo "Compile the code and generating necessary artifacts"
                bat "dir $DIRECTORY_PATH"  // list the contents of the directory 
            }
            post{
                success{
                    mail to:"reanyphasy@gmail.com",
                    subject:"Build Status Email",
                    body:"Build was successful!"
                }
            }
        }

        stage('Test')
         {
            steps 
            {
                bat "echo Unit tests"
                bat "echo Integration tests "
            }
        }

        stage('Code Quality Check')
         {
            steps
             {
                bat "echo Check the quality of the code"
            }
        }

        stage('Deploy') 
        {
            steps 
            {
                bat "echo Deploy the application to the testing environment: $TESTING_ENVIRONMENT"
            }
        }

        stage('Approval') 
        {
            steps 
            {
                script 
                {
                    bat "echo Waiting for manual approval..."
                    sleep(time: 10, unit: 'SECONDS')
                }
            }
        }

        stage('Deploy to Production')
         {
            steps 
            {
                bat "echo Deploying the code to the production environment: $PRODUCTION_ENVIRONMENT"
            }
        }
        stage("Complete")
         {
            steps 
            {
                bat "echo Completed."
            }
        }
    }
}
