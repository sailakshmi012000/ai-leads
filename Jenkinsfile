pipeline{
    agent any
    stages{
        stage('git-checkout'){
         when{
            branch "develop"
          }
         steps{
         echo "welcome to develop branch"
            }
        }
        stage('mvn build'){
            when{
                branch "test"
            }
            steps{
                echo "welcome to test branch"
            }
        }
        stage('production'){
            when{
                branch "main"
            }
            steps{
                echo "welcome to mains branch"
            }
        }
    }
}  
