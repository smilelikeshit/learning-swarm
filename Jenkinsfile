pipeline {

    agent none
    stages {
        stage('hello'){

            agent {
                docker 'alpine:latest'
            }

            steps {
                sh 'echo "HELLO WORLD"'
            }
        }
    }

}