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
                bat 'docker rm -f containertut5'
                bat 'docker run -d --name containertut5 -p 5000:5000 tut5'
            }
        }
    }
}
