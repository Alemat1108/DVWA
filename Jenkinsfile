pipeline {
    agent any
    options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    stages {
        stage('Scan') {
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh """
                        ${tool 'SonarQubeScanner'}/bin/sonar-scanner \
                        -Dsonar.sources=. \
                        -Dsonar.host.url=http://172.25.93.19:9000 \
                        -Dsonar.login=sonarqube-token
                    """
                }
            }
        }
    }
}



