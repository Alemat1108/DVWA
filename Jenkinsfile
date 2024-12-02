pipeline {
    agent any
    environment {
        SONARQUBE_SCANNER_HOME = tool 'Escaneo'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/Alemat1108/DVWA'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh """
                        ${env.SONARQUBE_SCANNER_HOME}/bin/sonar-scanner \
                        -Dsonar.sources=. \
                        -Dsonar.host.url=http://172.25.93.19:9000 \
                        -Dsonar.login=squ_364549662ef86dbe5c309d527ad1c7a9a10b5ec1
                    """
                }
            }
        }
    }
    post {
        always {
            echo 'Pipeline completed'
        }
        success {
            echo 'SonarQube analysis succeeded'
        }
        failure {
            echo 'SonarQube analysis failed'
        }
    }
}
