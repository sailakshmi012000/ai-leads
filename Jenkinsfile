ppipeline{
    agent any
    stages{
        stage("git checkout"){
            steps{
                git credentialsId: 'github-creds-', url: 'https://github.com/sailakshmi012000/my-app'
            }
        }
        stage("maven build"){
            steps{
                sh 'mvn clean package'
            }
        }
        stage("tomcat deploy"){
            steps{
               sshagent(['tomcat-dev']) {
                // copy war file
                sh 'scp -o StrictHostKeyChecking=no target/myweb-0.0.10.war ec2-user@172.31.90.230:/opt/tomcat9/webapps'
                //shutdown
                sh 'ssh ec2-user@172.31.90.230 /opt/tomcat9/bin/shutdown.sh'
                //start
                sh 'ssh ec2-user@172.31.90.230 /opt/tomcat9/bin/startup.sh'
                } 
            }
        }
    }
}
