pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Building the code using BuzzSumo."

            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit tests with Pytest and integration tests with Cypress and SoapUI."
            }
		post {
                success {
                    emailext attachLog: true,
                    subject: "Tests Completed Successfully",
		    body: "Unit and Integration Tests are completed successfully.",
                    to: "shehani.wickremasekera@gmail.com"  
                }
                failure {
                    emailext attachLog: true,
                    subject: "Tests Failed",
		    body: "Unit and Integration Tests got failed. Check the logs for details.",
                    to: "shehani.wickremasekera@gmail.com" 
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Performing code analysis with Coverity."
            }
        }
        stage('Security Scan') {
            steps {
                echo "Conducting security scan with Veracode."
            }
		post {
                success {
                   	emailext attachLog: true,
			subject: 'Security Scan Completed Successfully',
			body: 'Security Scan completed successfully.',
                    	to: 'shehani.wickremasekera@gmail.com'
                }
                failure {
                        emailext attachLog: true,
                        subject: 'Security Scan Failed',
			body: 'Security Scan failed. Check the logs for details.',
                        to: 'shehani.wickremasekera@gmail.com'      
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying to staging server on AWS EC2 instance."
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Executing integration tests in staging environment."
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying to production environment."
            }
        }
    }
    post {
        success {
 
           	emailext attachLog: true,
                subject: "Pipeline Successful",
                body: "The Jenkins pipeline completed successfully.",
               	to: "shehani.wickremasekera@gmail.com"
        }
        failure {
           	emailext attachLog: true,
                subject: "Pipeline Failed",
                body: "The Jenkins pipeline failed. Check the logs for details.",
                to: "shehani.wickremasekera@gmail.com" 
        }
    }
}
