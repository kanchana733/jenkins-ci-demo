pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                checkout scm
            }
        }

        stage('Setup Environment and Dependencies') {
            steps {
                sh 'apt-get update && apt-get install -y python3 python3-pip'
                sh 'python3 -m pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'python3 -m pytest test_calculator.py -v'
            }
        }
    }
}