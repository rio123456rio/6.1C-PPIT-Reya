pipeline {
    agent any
    stages {
        stage("Build") {
            steps {
                echo "Building using the automated tool : Maven"
            }
        }
        stage("Unit and Integration Tests") {
            steps {
                echo "Running unit and integration tests with automated tool: JUnit"
            }
            post {
                success {
                    emailext attachLog: true,
                    subject: "Successfully passed the testing!!",
                    body: "Unit and Integration Tests are completed using the tool Cypress.",
                    to: "reyamary00@gmail.com"  
                }
                failure {
                    emailext attachLog: true,
                    subject: "Couldn't pass the testing",
                    body: "Unit and Integration Tests have failed.",
                    to: "reyamary00@gmail.com" 
                }
            }
        }
        stage("Code Analysis") {
            steps {
                echo "Performing code analysis using the tool: CodeClimate"
            }
        }
        stage("Security Scan") {
            steps {
                echo "Undergoing security scan using the tool: Fortify Jenkins Plugin"
            }
            post {
                success {
                    emailext attachLog: true,
                    subject: "Security Scan has been successful.Good",
                    body: "Successfully passed the security scan through Fortify Jenkins Plugin.",
                    to: "reyamary00@gmail.com"
                }
                failure {
                    emailext attachLog: true,
                    subject: "Couldn't pass the Security Scan",
                    body: "Security Scan stage failed. Please make the necessary changes.",
                    to: 'reyamary00@gmail.com'      
                }
            }
        }
        stage("Deploy to Staging") {
            steps {
                echo "Deploying to AWS EC2 "
            }
        }
        stage("Integration Tests on Staging") {
            steps {
                echo "Successfully completed Integration Tests on Staging"
            }
        }
        stage("Deploy to Production") {
            steps {
                echo "Deploying to AWS EC2 Instance"
            }
        }
    }
    post {
        success {
            emailext attachLog: true,
            subject: "Pipeline status: Success",
            body: "Congrats! The pipeline shows a success status.",
            to: "reyamary00@gmail.com"
        }
        failure {
            emailext attachLog: true,
            subject: "Pipeline status: Failed",
            body: "The pipeline shows a failed status. Fix the issues.",
            to: "reyamary00@gmail.com" 
        }
    }
}
