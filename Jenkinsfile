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
                
                sh 'mvn clean deploy'
                sh 'mvn clean deploy -P cloudhub 
                -Danypoint.username="akw-contact" -Danypoint.password="MS3Password"'                
                }
             }
}
         
}
  }
}
