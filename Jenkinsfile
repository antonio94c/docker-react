/* Requires the Docker Pipeline plugin */
pipeline {
    agent { 
        label 'docker' 
    }
    stages {
        stage('Building our image') {
            steps {
                sh 'docker build -t antonio94c/view -f Dockerfile.dev .'
            }
        }
        stage('Run our Test') {
            steps{
               sh 'docker run antonio94c/view npm test -- --watchAll=false'
            }
        }stage('Go Up') {
            steps{
                sh 'docker-compose up'
            }
        }
        /*
        stage('Building our image') {
            steps {
                script {
                    dockerImage = docker.build "antonio94c/view:$BUILD_NUMBER"
                }
            }
        }
        stage('Run our image') {
            steps{
                script {
                    dockerImage.withRun(''){
                        sh 'npm run test -- --coverage'
                    }
                }
            }
        }
        /*
        stage('Deploy image'){
            steps{
                script {
                    docker.withRegistry('', 'dockerhub'){
                        dockerImage.push()
                    }
                }
            }
        }*/
    }
}