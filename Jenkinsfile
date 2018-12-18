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
         withCredentials([usernamePassword(credentialsId: 'anypoint.credentials', passwordVariable: 'anypoint_psw', usernameVariable: 'anypoint_usr')])
   {

       script {
                sh 'export ANYPOINT_USERNAME="akw-contact"'
                sh 'export ANYPOINT_PASSWORD="MS3Password"
                sh 'anypoint-cli'
                sh 'mvn clean deploy'
                
                }
             }
}
         
}
  }
}
