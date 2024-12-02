pipeline {
    agent any
    environment {
        SONARQUBE_SCANNER_HOME = tool 'Escaneo'
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Alemat1108/DVWA'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh "${env.SONARQUBE_SCANNER_HOME}/bin/sonar-scanner"
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

