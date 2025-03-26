pipeline{
    agent any
        stages{
            stage("git-checkout"){
                steps{
                    git branch: 'main', credentialsId: 'github-creds-', url: 'https://github.com/sailakshmi012000/ai-leads'
                }
            }
            stage("mvn-build"){
                steps{
                sh 'mvn clean package'
                }
            }
            stage("tomcat-deploy"){
                steps{
                    sshagent(['tomcat-dev']) {
                        // copy file
                        sh "scp -o StrictHostKeyChecking=no target/ai-leads.war ec2-user@172.31.90.230:/opt/tomcat9/webapps"
                        // stop tomcat
                        sh "ssh ec2-user@172.31.90.230 /opt/tomcat9/bin/shutdown.sh"
                        //start tomcat
                        sh "ssh ec2-user@172.31.90.230 /opt/tomcat9/bin/startup.sh"
                    }
                }
            }
        }
}
