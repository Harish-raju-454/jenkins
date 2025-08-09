pipeline {
    agent any

    environment {
        APP_ENV = "production"
        DEBUG = "false"
        APP_PORT = "8080"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Harish-raju-454/jenkins.git'
            }
        }

        stage('Build') {
            steps {
                echo "Building the project..."
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying application..."
                sh "java -jar target/*.jar"
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully ✅'
        }
        failure {
            echo 'Pipeline failed ❌'
        }
    }
}
