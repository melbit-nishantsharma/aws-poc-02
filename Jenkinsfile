pipeline {
    agent any
   
    stages {
        stage ('Initialize') {
            steps {
                dir ("/data/jenkins")
                checkout scm
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
                 echo "This step is: jenkins deploy to production"
            }
        }
    }
}