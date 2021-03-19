pipeline {
environment {
    registry = 'acchavez89/devops_project1'
    registryCredential = 'dockerhub_id'
    dockerImage = ''
  } 
  agent any 
  stages {
   stage('Cloning Git') {
      steps {
        git 'https://github.com/acchavez89/devops_course_proj1.git'
      }
    }

    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }

    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( 'https://hub.docker.com/repository/docker/acchavez89/devops_project1', registryCredential ) {
            dockerImage.push("$BUILD_NUMBER")
             dockerImage.push()
          }
        }
      }
    }

    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $imagename:$BUILD_NUMBER"
         sh "docker rmi $imagename:latest"
      }
    }
  }
}

      
      
     
    
   
  
