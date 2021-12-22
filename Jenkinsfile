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
     
  stage('Publish image to Docker Hub') {
  steps {
        withDockerRegistry([ credentialsId: "docker-hub-credentials", url: "https://index.docker.io/v1/" ]) {
          sh  'docker push alexgoffo200/pipeline:latest'
          sh  'docker push alexgoffo200/pipeline:$BUILD_NUMBER' 
            }
                  
            }
  }
    stage ('Deploy') {
    steps{
         sh '''
                ansible-playbook ansible-deployment.yml
            '''
    }
   
  }   
    }
}

