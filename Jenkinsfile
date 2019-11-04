pipeline {
    agent any 
    //stage('scm checkout'){
        
      // git credentialsId: 'Github', url: 'https://github.com/manikarnam/my-app-1.git'
    //}
  stages {
    stage('mvn package') {
      steps{  
      sh label: '', script: 'mvn clean package'
    }
}
    stage('Build Docker image'){
      steps{  
     sh 'docker build -t maniengg/jersy-maven .'
    }
}
    stage('push image to docker hub'){
      steps{
 
       withCredentials([string(credentialsId: 'docker-hubp', variable: 'dockerHubPwd')]) {
        sh "docker login -u maniengg -p ${dockerHubPwd}"
        }
   }
   sh 'docker push maniengg/jersy-maven'
      }
   }
}
