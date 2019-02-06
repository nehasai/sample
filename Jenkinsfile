import groovy.json

node {
    def json = readFile(file:'https://github.com/nehasai/sample.git/sample.json')

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
