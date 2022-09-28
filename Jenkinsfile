pipeline {
    agent any
 stages {
     stage("git checkout") {
         steps {
         git credentialsId: 'git-cred', url: 'https://github.com/saikishorpulla/myapp-2022.git'    
         }
     }
         stage("Maven Build") {
             steps {
                sh 'mvn clean package -DskipTests=true'
             }
         }
             stage("Dev Tomcat Deploy") {
                 steps {
                    sshagent(['git-creds']) {
                    // copy war
                    sh "scp -o StrictHostKeyChecking=no target/*.war ec2-user@172.31.1.48:/opt/tomcat9/webapps"
                    // stop tomcat
                    sh "ssh ec2-user@172.31.1.48 /opt/tomcat9/bin/shutdown.sh"
                    // start tomcat
                    sh "ssh ec2-user@172.31.1.48 /opt/tomcat9/bin/startup.sh"
                   } 
                 }
             }
         }
     }
