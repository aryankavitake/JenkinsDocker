pipeline {
    agent any

    triggers {
        pollSCM('H/2 * * * *')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
                echo 'GitHub code fetched successfully'
            }
        }

        stage('Build') {
            steps {
                bat 'docker build -t tut5 .'
            }
        }

        stage('Test') {
            steps {
                bat 'docker image inspect tut5'
                echo 'Docker image verified successfully'
            }
        }

        stage('Deploy') {
            steps {
                bat 'docker run -d --name containertut6 -p 5001:5000 tut5'
            }
        }
    }
}
