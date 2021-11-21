@Library('app-libs') _
pipeline{
    agent any
    stages{
        stage('SCM Checkout'){
            steps{
                git branch: 'dev', url: 'https://github.com/Harish369369/myapp.git'
            }
       }
       stage('Maven Build'){
            steps{
                sh 'mvn clean package'
            }
       }
       stage('Deploy to  Tomcat Development'){
            
           steps{
               tomcat-deploy("172.31.32.109","tomcat-dev","myweb")
            }
       }
    }
    post {
        always {
            cleanWs()
       }
    }
}
