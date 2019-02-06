import groovy.json.JsonSlurper
def json = readFile(file:'sample.json')
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
}
}
