pipeline {
    agent any

    stages {
        stage('Install dependencies') {
            steps {
                echo "Installing Python dependencies..."
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                echo "Running tests..."
                sh 'pytest --maxfail=1 --disable-warnings -q'
            }
        }
    }
}
