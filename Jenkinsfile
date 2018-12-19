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
            script {
                withCredentials([usernamePassword(credentialsId: 'anypoint.credentials', 
                passwordVariable: 'anypoint_psw', usernameVariable: 'anypoint_usr')])
            {
                    sh 'anypoint-cli'
                    sh 'export ANYPOINT_USERNAME="anypoint_usr"'
                    sh 'export ANYPOINT_PASSWORD="anypoint_psw"'
                    sh 'anypoint-cli'
                    sh 'anypoint-cli --username="anypoint_usr"'
                    sh 'mvn deploy -P -Danypoint.username=${anypoint_usr} -Danypoint.password=${anypoint_psw}' 
                }

            

                     
        }
    }
}
}

