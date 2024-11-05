pipeline {
    agent any
 
    environment {
        // Define Python version if using a specific one
        PYTHON_VERSION = 'python3'
    }
 
    stages {
        stage('Clone Repository') {
            steps {
                // Clone the repository
                git url: 'https://github.com/bhaskar-prasad/Demo', branch: 'main'
            }
        }
 
 
        stage('Deploy') {
            steps {
                // Dummy deploy step (replace with actual deployment commands)
                echo 'Deploying the application...'
            }
        }
    }
 
    post {
        always {
            echo 'Cleaning up...'
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed. Please check the errors.'
        }
    }
}
