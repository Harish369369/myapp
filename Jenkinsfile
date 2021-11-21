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
                tomcatdeploy("3.110.94.187","tomcat-dev","myweb")
            }
       }
            steps{
        post {
        always {
            cleanWs()
                }
            } 
        }
    }
}
