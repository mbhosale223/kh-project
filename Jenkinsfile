pipeline {
    agent any
    environment {
        registry = "iamsauravsingh/python-app"
        registryCredential = 'dockerhub'
    }

    stages {
        stage('git checkout') {
            steps {
                git branch: 'project-1', url: 'https://github.com/iamsauravsingh7/kh-project.git'
            }
        }
        
        stage('Build docker image') {
            steps {
                script {
                  dockerImage = docker.build registry + ":v$BUILD_NUMBER"
              }
            }
        }
        stage('Upload Image'){
          steps{
            script {
              docker.withRegistry('', registryCredential) {
                dockerImage.push("v$BUILD_NUMBER")
                dockerImage.push('latest')
              }
            }
          }
        }
        stage('Remove Unused docker image') {
          steps{
            sh "docker rmi $registry:v$BUILD_NUMBER"
          }
        }
        stage('Deploying container to Kubernetes') {
            agent {label 'control-plane'}
                steps {
                     sh "kubectl apply -f python-deploy.yaml -f python-svc.yaml"
            }
        }      
    }
}
