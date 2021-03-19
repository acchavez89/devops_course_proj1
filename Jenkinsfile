pipeline {

stages{  
 stage('Clone repository') {
   checkout scm
 }
  
 stage('Build image') {
   app =  docker.build("acchavez89/devops_course_proj1")
 }
  
 stage('Push image') {
     docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_id') {
         app.push("${env.BUILD_NUMBER}")
         app.push("latest")
	 }
 }
}
}
      
      
     
    
   
  
