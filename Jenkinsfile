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
                script {
                withCredentials([usernamePassword(credentialsId: 'anypoint.credentials', 
                passwordVariable: 'anypoint_psw', usernameVariable: 'anypoint_usr')])
                {
                    sh 'anypoint-cli'
                    sh 'export ANYPOINT_USERNAME="anypoint_usr"'
                    sh 'export ANYPOINT_PASSWORD="anypoint_psw"'
                    sh 'anypoint-cli'
                    sh 'anypoint-cli --username="anypoint_usr"'
                    sh 'anypoint-cli --username=${anypoint_usr} --password=${anypoint_psw} --environment='+"$anypoint_environment"+' runtime-mgr 
                    cloudhub-application modify --runtime '+"$muleversion"+' '+"$applicationName"+' '+"$artifactName"+'-'+"$version"+'.zip'
                } 
            }

            

                     
        }
    }
}
}



