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
                sh 'python3 -m pip install --user -r requirements.txt || python -m pip install --user -r requirements.txt || pip install --user -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'python3 -m pytest test_calculator.py -v || python -m pytest test_calculator.py -v || pytest test_calculator.py -v'
            }
        }
    }
}