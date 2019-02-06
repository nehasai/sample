import groovy.json.JsonSlurperClassic

node {
    def json = readFile(file:'https://github.com/nehasai/sample.git/sample.json')
    def data = new JsonSlurperClassic().parseText(json)

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
