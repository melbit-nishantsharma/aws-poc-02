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
                emailext body: "<p>STATUS-tobeupdated: Job \'${env.JOB_NAME} [${env.BUILD_ID}]\':</p>
    <p>Check console output at "<a href="${env.BUILD_URL}">${env.JOB_NAME} [${env.BUILD_ID}]</a>"</p>", subject: "Job \'${env.JOB_NAME} [${env.BUILD_ID}]\'", to: 'nishant.sharma@melbourneit.com.au'
            }
        }
        stage ('Promote to Prod?') {
            steps {
                timeout(time:5, unit:'DAYS') {
                input (id: 'proceed', message: 'Promote to Production?')
                }
            }
        }
        stage ('Deploy to Prod') {
            steps {
                 echo "This step is: jenkins deploy to prod"
            }
        }
    }
}