pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                checkout scm
            }
        }

        stage('Setup Dependencies') {
            steps {
                sh 'docker run --rm -v ${WORKSPACE}:/app -w /app python:3.9-slim pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'docker run --rm -v ${WORKSPACE}:/app -w /app python:3.9-slim python -m pytest test_calculator.py -v --html=reports/report.html --self-contained-html'
            }
        }
    }
}