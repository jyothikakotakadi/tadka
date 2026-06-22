pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t tadka-express .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop tadka-express || true
                docker rm tadka-express || true

                docker run -d \
                --name tadka-express \
                -p 8090:80 \
                tadka-express
                '''
            }
        }
    }
}
