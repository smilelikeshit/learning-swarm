pipeline {

    agent none
    options {
        timeout(time: 5, unit: 'MINUTES') 
    }

    stages {

        stage('Create passwd') {
            agent any
            steps {
                sh """touch /tmp/tmp_passwd && echo \$(getent passwd \$USER) > /tmp/tmp_passwd
                """
            }
        }

        stage('hello'){

            when { 
                branch 'master'    
            }

            agent {
                docker {
                      image 'alpine:latest'
                      //args '-v /tmp/tmp_passwd:/etc/passwd'
                      args '-u root'
                } 
            }

            steps {
                sshagent(credentials : ['629476ac-5086-4fd9-b793-d6296863c745']) {
                    sh "apk add openssh"
                    sh 'ssh -t -t  root@165.22.58.224 -o StrictHostKeyChecking=no "echo pwd"'
                }
            }
        }
    }

    post {
        always {
            cleanWS()
        }
    }

}