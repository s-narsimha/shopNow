pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git url: 'https://github.com/s-narsimha/shopNow.git', branch: 'main'
            }
        }

        stage('List Files') {
            steps {
                sh 'ls -la'
            }
        }
    }
}
