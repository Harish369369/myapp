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
       stage('Tomcat deploy'){
            steps{
                sshagent(['tomcat-dev']) {
                sh "scp -o StrictHostKeyChecking=no target/myweb*.war ec2-user@172.31.32.109:/opt/tomcat8/webapps/"
                sh "ssh ec2-user@172.31.32.109 /opt/tomcat8/bin/startup.sh"
                }
            }
            post {
  always {
        cleanWs()
            }
        }
       }
    }
}
