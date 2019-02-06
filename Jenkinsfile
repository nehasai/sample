node {
def json = readFile(file:'sample.json')
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
