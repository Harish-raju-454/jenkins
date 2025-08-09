pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Set Up Python') {
            steps {
                sh '''
                    python3 --version
                    python3 -m pip install --upgrade pip
                    python3 -m pip install -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                    python3 -m pytest --maxfail=1 --disable-warnings -q
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Build and tests passed successfully!'
        }
        failure {
            echo '❌ Build or tests failed!'
        }
    }
}
