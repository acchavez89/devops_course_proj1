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
        git([url:  'https://github.com/acchavez89/devops_course_proj1.git', branch: 'main', credentialsId: 'GitHubCredentials2'])
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
          docker.withRegistry( '', registryCredential ) {
             dockerImage.push()
          }
        }
      }
    }

  }
}

      
      
     
    
   
  
