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
                git credentialsId: '8418a4c3-8ef6-4416-a871-b491f0b8e9be', branch: 'main', url: 'https://github.com/priyarathod05/jankin_repo.git'
            }
        }

        stage('Set Up PHP Environment') {
            steps {
                echo 'Setting up PHP environment...'
                // Check PHP version
                sh '''
                php -v
                composer install
                '''
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running PHPUnit tests...'
                // Run PHPUnit tests with your configuration file
                sh './vendor/bin/phpunit --configuration phpunit.xml'
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
