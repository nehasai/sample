import groovy.json.JsonSlurper
pipeline {
    agent any
stages {
        stage('test') {
               steps {
                   script {
                       sh 'mvn clean test'
                    }                
                } 
            }
        stage('build') {
            steps {
                sh 'mvn clean install package'
                }
          }
         stage('read json')
         {
        steps {
       def json = readFile(file:'sample.json')
}
}
}
}
