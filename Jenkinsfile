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
                sh 'python3 -m pip install --break-system-packages -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                // Ensure the reports directory exists and run pytest with HTML output
                sh 'mkdir -p reports'
                sh 'python3 -m pytest --html=reports/report.html --self-contained-html test_calculator.py -v'
            }
        }
    }

    post {
        always {
            // Archive the HTML report so it appears under Build Artifacts in Jenkins
            archiveArtifacts artifacts: 'reports/report.html', allowEmptyArchive: true
        }
    }
}