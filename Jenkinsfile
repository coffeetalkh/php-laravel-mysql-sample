pipeline {
    agent { dockerfile true }
    parameters{
        string(defaultValue: 'test-name', description: '', name: 'NAME')
        string(defaultValue: 'test-adjective', description: '', name: 'ADJECTIVE')
        string(defaultValue: 'test-plural', description: '', name: 'PLURAL_NOUN')
    }
    stages {
        stage('Build') {
            steps{
                sh 'cp .env.example .env'
                echo 'Hello Mr/Ms ${NAME}'
            }
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
        stage('Clean-up') {
            paralle {
                steps('Dangling Containers') {
                  sh 'docker ps -q -f status=exited | xargs --no-run-if-empty docker rm'
                }
                steps('Dangling Images') {
                  sh 'docker images -q -f dangling=true | xargs --no-run-if-empty docker rmi'
                }
                steps('Dangling Volumes') {
                  sh 'docker volume ls -qf dangling=true | xargs -r docker volume rm'
                }
            } 
        }
    }
}
