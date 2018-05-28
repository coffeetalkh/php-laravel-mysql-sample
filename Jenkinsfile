pipeline {
    agent { dockerfile true }
    parameters{
        string(defaultValue: true, description: '', name: 'NAME')
        string(defaultValue: true, description: '', name: 'ADJECTIVE')
        string(defaultValue: true, description: '', name: 'PLURAL_NOUN')
    }
    stages {
        stage('Build') {
                sh 'cp .env.example .env'
                echo 'Hello Mr/Ms ${NAME}'
                sh 'composer update'
                sh 'php artisan serv'
        }
        stage('Test') {
            parallel {
                stage('Unit-Test'){
                   steps {
                       echo 'Unit Testing..'
                       echo 'You can join with this ${ADJECTIVE} adjective.'
                   }
                 }
                 stage('Smoke-test'){
                     steps {
                         echo 'Smoke testing...'
                     }
                 }
                 stage('Acceptance-test'){
                     steps {
                         echo 'Acceptance testing...'
                     }
                 }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
        }
    }
}
