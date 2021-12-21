pipeline {
    agent any
 stages {
  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t newimage:latest .' 
                  sh 'docker tag newimage coursework2/newimage:latest'
                sh 'docker tag newimage coursework2/newimage:$BUILD_NUMBER'
               
          }
        }
     
  stage('Publish image to Docker Hub') {
          
            steps {
        withDockerRegistry([ credentialsId: "docker-hub-credentials", url: "https://hub.docker.com/" ]) {
          sh  'docker push coursework2/newimage:latest'
          sh  'docker push coursework2/newimage:$BUILD_NUMBER' 
        }
                  
          }
        }
     
      stage('Run Docker container on Jenkins Agent') {
             
            steps {
                sh "docker run -d -p 4030:80 coursework2/newimage"
 
            }
        }
 stage('Run Docker container on remote hosts') {
             
            steps {
                sh "docker -H ssh://jenkins@172.31.28.25 run -d -p 4001:80 coursework2/newimage"
 
            }
        }
    }
}
