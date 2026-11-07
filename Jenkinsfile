pipeline {
    agent any

    stages {
        stage('Setup') {
            steps {
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install -r requirements.txt
                '''
            }
        }
        stage('Run App') {
            steps {
                sh '''
                    . venv/bin/activate
                    python app.py
                '''
            }
        }
        stage('Test') {
            steps {
                sh '''
                    . venv/bin/activate
                    pytest -v
                '''
            }
        }
    }

    post {
        success { echo 'Sab tests pass! ✅' }
        failure { echo 'Tests fail hue ❌' }
    }
}
