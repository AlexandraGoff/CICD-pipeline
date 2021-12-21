pipeline{
    agent any
    stages{
        stage('SCM Checkout'){
            steps{
                git credentialsId: '76f70f5c-e612-45b2-8861-e9652506abf3', url: 'https://github.com/AlexandraGoffova/Coursework-Pipeline2.git'
            }
        }
        stage('Build docker image'){
            steps{
             sh 'docker build -t coursework2/image'
            }
        }
       
}
