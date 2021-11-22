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
                tomcatdeploy("3.6.41.15:8080","tomcat-dev","*")
            }
       }
    }
}
