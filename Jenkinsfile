pipeline {
    agent any

    environment {
        // Define PHP version for setup if needed
        PHP_VERSION = '8.2.12'  // Example PHP version, change as required
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Checking out the code from Git repository...'
                // Using Username/Password credentials for HTTP-based Git authentication
                git credentialsId: 'git-username-password', branch: 'main', url: 'https://github.com/priyarathod05/jankin_repo.git'
            }
        }
        stage('Build Project') {
            steps {
                echo 'Building the project...'
                // Add any build steps for your project if necessary
            }
        }
    }

    post {
        success {
            echo 'Build and tests succeeded!'
        }
        failure {
            echo 'Build or tests failed!'
        }
        always {
            echo 'Cleaning up workspace...'
            cleanWs()  // Cleans up the workspace after the build
        }
    }
}
