
pipeline {
    agent any

    environment {
        PYTHON_VERSION = 'python3'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/siddharthTricon/DemoGit', branch: 'main'
            }
        }

        stage('Setup Environment') {
            steps {
                sh "${PYTHON_VERSION} -m venv venv"
                sh ". venv/bin/activate && pip install -r requirements.txt"
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                sh ". venv/bin/activate && python setup.py sdist" // Creates a source distribution
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh ". venv/bin/activate && pytest --junitxml=report.xml"
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                sh "scp -i /path/to/key.pem dist/*.tar.gz ubuntu@server-ip:/path/to/deployment"
                sh "ssh -i /path/to/key.pem ubuntu@server-ip 'tar -xzvf /path/to/deployment/*.tar.gz -C /path/to/app'"
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
