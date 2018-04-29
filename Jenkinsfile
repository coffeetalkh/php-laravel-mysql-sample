pipeline {
    agent { dockerfile true }
    stages {
        stage('Build') {
            steps {
                sh 'cp .env.example .env'
                sh 'composer update'
                sh 'php artisan serv'
            }
        }
    }
}
