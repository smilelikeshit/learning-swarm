pipeline {

    agent none
    stages {
        stage('hello'){

             when { 
                not { 
                    branch 'development' 
                }
            }

            agent {
                docker 'alpine:latest'
            }

            steps {
                sh 'echo "HELLO WORLD"'
            }
        }
    }

    

}