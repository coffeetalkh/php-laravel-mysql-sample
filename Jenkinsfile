pipeline {
    agent { dockerfile true }
    stages {
        stage('Test') {
            steps {
                sh 'cp .env.example .env'
                sh 'composer update'
                sh 'php artisan serv'
            }
        }
    }
}
