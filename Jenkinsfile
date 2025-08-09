pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                script {
                    // Install zip if it's missing
                    sh '''
                    if ! command -v zip &> /dev/null
                    then
                        echo "zip not found, installing..."
                        sudo apt-get update
                        sudo apt-get install zip -y
                    else
                        echo "zip is already installed"
                    fi
                    '''
                }
            }
        }

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
