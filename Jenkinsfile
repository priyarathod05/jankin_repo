pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/priyarathod05/jankin_repo.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'composer install' // Replace with your project dependencies command
            }
        }
        stage('Run Tests') {
            steps {
                sh 'php artisan test' // Replace with your test command
            }
        }
    }
}
