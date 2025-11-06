pipeline {
    agent any

    stages {

        stage('Build & Test in Docker') {
            steps {
                script {
                    docker.image('python:3.10').inside {
                        sh 'pip install --upgrade pip'
                        sh 'pip install -r requirements.txt'
                        sh 'pytest --junitxml=report.xml'
                    }
                }
            }
        }

        stage('Publish Report') {
            steps {
                junit 'report.xml'
            }
        }
    }
}
