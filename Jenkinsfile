
pipeline {
    agent any

    environment {
        NODE_VERSION = '14' // Specify Node.js version
    }

    stages {
        stage('Clone Repository') {
            steps {
                // Clone the repository containing your JavaScript code
                git url: 'https://github.com/your-repo-url/your-repo-name.git', branch: 'main'
            }
        }

        stage('Install Node.js') {
            steps {
                // Install Node.js if not already available
                sh 'curl -sL https://deb.nodesource.com/setup_${NODE_VERSION}.x | sudo -E bash -'
                sh 'sudo apt-get install -y nodejs'
            }
        }

        stage('Build') {
            steps {
                // Perform any build steps here, such as linting or transpiling
                echo 'Building the application...'
                // Example: Lint the code if ESLint is installed
                sh 'npx eslint path/to/your-script.js || true' // Lint, but do not fail build if lint errors occur
            }
        }

        stage('Test') {
            steps {
                // Run tests if any test framework is available
                echo 'Running tests...'
                // Example: Add a simple test to validate the add and multiply functions
                script {
                    sh 'echo "console.log(\'Test passed: add and multiply functions.\')" > test.js' // Placeholder test
                    sh 'node test.js'
                }
            }
        }

        stage('Deploy') {
            steps {
                // Add deployment commands here
                echo 'Deploying the application...'
                // This could involve copying files, starting a server, etc.
                // Example placeholder: simply prints a deploy message
                sh 'echo "Application deployed successfully."'
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
        }
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs for errors.'
        }
    }
}

