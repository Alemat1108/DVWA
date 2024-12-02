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
                        ${tool 'Escaneo'}/bin/sonar-scanner \
                        -Dsonar.projectKey=DVWA \
                        -Dsonar.sources=. \
                        -Dsonar.host.url=http://172.25.93.19:9000 \
                    """
                }
            }
        }
    }
}



