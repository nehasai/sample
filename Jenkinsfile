pipeline {
    agent any
    stages {
        stage('build') {
            script {
                sh 'mvn clean install package'
                }
            }

        stage('test') {
            script {
                sh 'mvn clean test'

            }
        }
        stage('deploy to  CloudHub') {
            script {
                applicationName = "$artifactName"+'-'+"dev"
                echo "${applicationName}"
                withCredentials([usernamePassword(credentialsId: 'anypoint.credentials', 
                passwordVariable: 'anypoint_psw', usernameVariable: 'anypoint_usr')])
                {
                    sh 'export ANYPOINT_USERNAME="akw-contact"'
                    sh 'export ANYPOINT_PASSWORD="MS3Password"'
                    sh 'anypoint-cli'
                }
            }         
        }
    }
}
