@Library("sailibs") _
pipeline{
    agent any
    stages{
        stage("Maven Build"){
            when {
                branch "develop"
            steps{
                sh 'mvn clean package -DskipTests=true'
            }
        }
        stage(" Dev Tomcat Deploy"){
            steps{
                tomcatDeploy("172.31.1.234","ec2-user","tomcat-dev")
            }
        }
    }
}
