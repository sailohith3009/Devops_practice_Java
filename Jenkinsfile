pipeline {
    agent any

    stages {
        stage('Remove all containers') {
            steps {
                sh 'docker ps -aq | xargs docker stop | xargs docker rm'
            }
        }
        stage('Build Image') {
            steps {
                sh '''docker build -t lohith30/customnginx .
                '''
            }
        }
        stage('Start Docker Container') {
            steps {
                sh 'docker run -itd -p 8081:80 --name=mynginx lohith30/customnginx'
            }
        }
        stage('Success Message') {
            steps {
                echo 'Successfully completed is pipeline'
            }
        }
    }
}
