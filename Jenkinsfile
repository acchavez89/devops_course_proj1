pipeline {
environment {
    registry = 'acchavez89/devops_project1'
    registryCredential = ‘dockerhub_id’
    dockerImage = ‘latest’
  } 
  agent any 
  stages {
   stage('Cloning Git') {
      steps {
        git([url: 'https://github.com/acchavez89/devops_course_proj1.git', branch: 'main', credentialsId: 'GitHubCredentials2'])
      }
    }

    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build mypractice
        }
      }
    }

    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( 'https://hub.docker.com/repository/docker/acchavez89/devops_project1', registryCredential ) {
            dockerImage.push("$BUILD_NUMBER")
             dockerImage.push('latest')
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

      
      
     
    
   
  
