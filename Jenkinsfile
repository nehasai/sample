pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'mvn clean install package'
                }
            }

        stage('test') {
            steps {
                sh 'mvn clean test'

            }
        }
        stage('deploy to  CloudHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'anypoint.credentials', 
                passwordVariable: 'anypoint_psw', usernameVariable: 'anypoint_usr')])
                {
                
                    sh 'export ANYPOINT_USERNAME="anypoint_usr"'
                    sh 'export ANYPOINT_PASSWORD="anypoint_psw"'
                    sh 'anypoint-cli'
                }
            }

                     
        }
    }
}
