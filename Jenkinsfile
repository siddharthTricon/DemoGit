pipeline {
    agent any
 
    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from your version control system
                git url: 'https://github.com/siddharthTricon/DemoGit.git', branch: 'main'
            }
        }
 
        stage('Install Dependencies') {
            steps {
                script {
                    // Upgrade pip and install dependencies globally
                    sh '''
                        python -m pip install --upgrade pip
                    '''
                }
            }
        }
 
        stage('Run Tests') {
            steps {
                script {
                    // Run tests using unittest
                    sh 'python test_calculator.py'
                }
            }
        }
    }
 
    post {
        always {
            // Clean up the workspace after the build
            cleanWs()
        }
        success {
            echo 'Tests passed successfully!'
        }
        failure {
            echo 'Tests failed!'
        }
    }
}
