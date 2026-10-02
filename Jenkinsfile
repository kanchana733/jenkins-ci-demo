pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Setup Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'pytest test_calculator.py --v --html=reports/report.html --self-contained-html'
            }
        }

        stage('Archive Report') {
            steps {
                archiveArtifacts artifacts: 'reports/report.html', fingerprint: true
            }
        }
    }
}