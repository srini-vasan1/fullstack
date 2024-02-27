pipeline {
    agent any

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
                            -Dsonar.projectKey=fullstack \
                            -Dsonar.sources=src \
                            -Dsonar.host.url=http://192.168.0.106:9000
                            -Dsonar.login=sqa_2a6c334b3644b30a22598079e6c0668eec18a9ce

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
