pipeline {
    agent any

    stages {
        stage ('Initialize') {
            checkout scm
        }
        stage ('Build') {
            echo timestamp=$(date +"%m%d%Y_%H%M")
            echo "$timestamp: $GIT_BRANCH: jenkins build" >> sample.txt
        }
        stage ('Test') {
            echo "Testing passed"
        }
        stage ('Promote to Prod?') {
            timeout(time:5, unit:'DAYS') {
                input (id: 'proceed', message: 'Promote to Production?')
            }
        }
        stage ('Deploy to Prod') {
            echo timestamp=$(date +"%m%d%Y_%H%M")
            echo "$timestamp: $GIT_BRANCH: jenkins deploy to production" >> sample.txt
        }

    }
}