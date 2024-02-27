pipeline {
    agent any

    environment {
        scannerHome = tool 'sonarqube-b'
    }

    stages {
        stage('SonarQube Analysis') {
            steps {
                script {
                    withSonarQubeEnv('sonarqube-b') {
                        sh """
                            ${scannerHome}/bin/sonar-scanner \
                            -Dsonar.projectKey=nodeapp \
                            -Dsonar.sources=src \
                            -Dsonar.host.url=http://192.168.0.106:9000
                        """
                    }
                }
            }
        }
    }
}