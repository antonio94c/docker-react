pipeline {
    agent { 
        label 'docker' 
    }
    stages {
        stage('Clean Docker envoironment'){
            steps {
                sh 'docker system prune -a -f'
            }
        }
        stage('Building our image') {
            steps {
                sh 'docker build -t antonio94c/fronted .'
            }
        }
        /*stage('Run our Test') {
            steps{
               sh 'docker run antonio94c/fronted npm test -- --watchAll=false'
            }
        }*/
        stage('Clean after build and test'){
            steps{
                sh 'rm -rf workspace/Fronted/'
            }
        }
        stage('Go Up') {
            steps{
                sh 'docker run antonio94c/fronted'
            }
        }
    }
}