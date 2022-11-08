/* Requires the Docker Pipeline plugin */
pipeline {
    agent { 
        label 'docker' 
    }
    stages {
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