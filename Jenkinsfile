pipeline {
    agent any
    tools {
        maven 'maven3'
    }
    stages {
        stage('Install') {
            steps {
                sh "mvn clean test"
            }
        }
    }
}
