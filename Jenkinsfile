pipeline {
    agent { 
        label 'jenkins-s'
    }

    environment {
        scannerHome = tool 'sonarqube'
    }

    stages {
        stage('SonarQube Analysis') {
            steps {
                script {
                    withSonarQubeEnv('sonarqube') {
                        sh """
                            ${scannerHome}/bin/sonar-scanner \
                            -Dsonar.projectKey=jenkins-node \
                            -Dsonar.sources=src \
                            -Dsonar.host.url=http://192.168.0.106:9000
                        """
                    }
                }
            }
        }

        stage('Post-Analysis') {
            steps {
                echo 'SonarQube analysis completed successfully!'
            }
        }
    }
}
