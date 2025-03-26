pipeline{
    agent any

    stages{
        stage("Maven Build"){
            when{
                branch "develop"
            }
            steps{
                echo "maven"
            }
        }
        stage("Tomcat Deploy - Dev"){
            when{
                branch "test"
            }
            steps{
               echo "deploy tomcat"
                }
            }
        }

    
}
