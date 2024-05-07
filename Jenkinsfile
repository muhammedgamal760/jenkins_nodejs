pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/muhammedgamal760/jenkins_nodejs_example.git'
            }
        }
        stage('docker build'){
            steps{
                //adding credentials
                withCredentials([usernamePassword(credentialsId: 'docker', passwordVariable: 'DOCKER_PASS', usernameVariable: 'DOCKER_USER')]) {
                sh "sudo docker login -u ${env.DOCKER_USER} -p ${env.DOCKER_PASS}"}
                //building docker file
                sh 'sudo docker build . -t muhammedgamal/jenkins'
            }
        }
        stage('docker push'){
            steps{
                //pushing image
                sh 'sudo docker push muhammedgamal/jenkins'
            
        }
        }
        stage('docker run'){
            steps{
                //run docker
                sh 'sudo docker run -d -p 3000:3000 muhammedgamal/jenkins'
            }
        }
        
    }
}
