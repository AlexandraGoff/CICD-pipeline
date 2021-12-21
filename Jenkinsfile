pipeline {
    agent any
 stages {
  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t newImage:latest .' 
                  sh 'docker tag newImage coursework2/newImage:latest'
                sh 'docker tag newImage coursework2/newImage:$BUILD_NUMBER'
               
          }
        }
     
  stage('Publish image to Docker Hub') {
          
            steps {
        withDockerRegistry([ credentialsId: "dockerHub", url: "alexgoffo200/pipeline" ]) {
          sh  'docker push coursework2/newImage:latest'
          sh  'docker push coursework2/newImage:$BUILD_NUMBER' 
        }
                  
          }
        }
     
      stage('Run Docker container on Jenkins Agent') {
             
            steps {
                sh "docker run -d -p 4030:80 coursework2/newImage"
 
            }
        }
 stage('Run Docker container on remote hosts') {
             
            steps {
                sh "docker -H ssh://jenkins@172.31.28.25 run -d -p 4001:80 coursework2/newImage"
 
            }
        }
    }
}
