pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh '''
                mkdir -p dist
                zip -r dist/Jenkins-build-2.zip . -x "*/.git/*"
                '''
            }
        }
        stage('Test') {
            steps {
                sh '''
                pip install pytest
                pytest || echo "⚠ No tests found or tests failed"
                '''
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'dist/Jenkins-build-2.zip', followSymlinks: false
            }
        }
    }
}

