pipeline {
    agent { 
        label 'local'
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
                            -Dsonar.sources=/opt/jenkins/workspace/fullstack/backend,/opt/jenkins/workspace/fullstack/frontend \
                            -Dsonar.host.url=http://192.168.0.100:9000
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
