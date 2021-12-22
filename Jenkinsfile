pipeline {
    agent any
 stages {
  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t pipeline:latest .' 
                  sh 'docker tag pipeline alexgoffo200/pipeline:latest'
                sh 'docker tag pipeline alexgoffo200/pipeline:$BUILD_NUMBER'
               
          }
        }
     
<<<<<<< HEAD
  stage('Publish image to Docker Hub') {
  steps {
=======
  stage('Publish imaged to Docker Hub') {
          
            steps {
>>>>>>> c23ee80 (test)
        withDockerRegistry([ credentialsId: "docker-hub-credentials", url: "https://index.docker.io/v1/" ]) {
          sh  'docker push alexgoffo200/pipeline:latest'
          sh  'docker push alexgoffo200/pipeline:$BUILD_NUMBER' 
            }
                  
            }
  }
     
   stage('Run Docker container test') {
             
            steps {
                sh "docker run -d -p 4030:80 alexgoffo200/pipeline"
 
            }
        }
 
    }
}
