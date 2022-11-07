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
        stage('Deploy image'){
            script {
                docker.withRegistry('', 'dockerhub'){
                    dockerImage.push()
                }
            }
        }
    }
}