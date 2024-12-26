pipeline {
    agent any

    environment {
        PHP_VERSION = ' 8.2.12' // Set the PHP version
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Checking out the code...'
                git branch: 'main', url: 'https://github.com/priyarathod05/jankin_repo.git'
            }
        }

        stage('Set Up PHP Environment') {
            steps {
                echo 'Setting up PHP environment...'
                sh '''
                php -v
                composer install
                '''
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running PHPUnit tests...'
                sh './vendor/bin/phpunit --configuration phpunit.xml'
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
            cleanWs() // Cleans up the workspace after build
        }
    }
}
