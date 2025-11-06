pipeline {
    agent any

    stages {
        stage('Setup Virtual Env') {
            steps {
                sh 'python3 -m venv venv'
                sh './venv/bin/pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh './venv/bin/pytest --junitxml=report.xml'
            }
        }

        stage('Publish Report') {
            steps {
                junit 'report.xml'
            }
        }
    }
}
