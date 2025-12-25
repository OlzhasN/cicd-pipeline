pipeline {
    agent {
        docker {
            image 'node:18-alpine'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'chmod +x scripts/build.sh'
                sh 'scripts/build.sh'
            }
        }

        stage('Test') {
            steps {
                sh 'chmod +x scripts/test.sh'
                sh 'scripts/test.sh'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t olzhasn/mybuildimage:latest .'
            }
        }
    }
}
