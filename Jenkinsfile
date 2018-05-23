pipeline {
    agent { dockerfile true }
    parameters{
        string(defaultValue: true, description: '', name: 'NAME')
        string(defaultValue: true, description: '', name: 'ADJECTIVE')
        string(defaultValue: true, description: '', name: 'PLURAL_NOUN')
    }
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
