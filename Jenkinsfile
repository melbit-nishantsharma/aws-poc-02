pipeline {
    agent any

    stages {
        stage ('Initialize') {
            steps {
                checkout scm
            }  
        }
        stage ('Build') {
            steps {
                echo timestamp=$(date +"%m%d%Y_%H%M")
                echo "$timestamp: $GIT_BRANCH: jenkins build" >> sample.txt
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
                echo timestamp=$(date +"%m%d%Y_%H%M")
                echo "$timestamp: $GIT_BRANCH: jenkins deploy to production" >> sample.txt
            }
        }
    }
}