pipeline {
    agent any
   
    stages {
        stage ('Initialize') {
            steps {
                dir ("/data/jenkins") {
                checkout scm
                }
            }  
        }
        stage ('Build') {
            steps {
                echo "This job is: jenkins build"
            }
        }
        stage ('Test') {
            steps {
                echo "Testing passed"
                emailext (
                    (to: 'nishant.sharma@melbourneit.com.au',
                     subject: "Job '${env.JOB_BASE_NAME}' (${env.BUILD_NUMBER}) is waiting for input",
                     body: "Please go to console output of ${env.BUILD_URL} to approve or Reject.");
                     def userInput = input(id: 'userInput', message: 'Do you want to proceed to prod?', ok: 'Yes')
                )
            }
        }
        /*
        stage ('Promote to Prod?') {
            steps {
                timeout(time:5, unit:'DAYS') {
                input (id: 'proceed', message: 'Promote to Production?')
                }
            }
        }
        */
        stage ('Deploy to Prod') {
            steps {
                 echo "This step is: jenkins deploy to prod"
            }
        }
    }
}