pipeline {

    agent none
    options {
        timeout(time: 1, unit: 'HOURS') 
    }

    stages {
        stage('hello'){

             when { 
                branch 'master'    
            }

            agent {
                docker 'gotechnies/alpine-ssh'
            }

            steps {
                sshagent(credentials : ['629476ac-5086-4fd9-b793-d6296863c745']) {
                    sh "echo pwd"
                    sh 'ssh -t -t uroot@165.22.58.224 -o StrictHostKeyChecking=no "echo pwd"'
                }




            }
        }
    }

    post {
        always {
            deleteDir()
        }

    }



}