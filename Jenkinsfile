pipeline {
    agent {
        docker {
            image 'php:8.2.12-cli'
            args '-v /var/jenkins_home:/var/jenkins_home' // Mount Jenkins home to persist workspace
        }
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
                curl -sS https://getcomposer.org/installer | php
                mv composer.phar /usr/local/bin/composer
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
