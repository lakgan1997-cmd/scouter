pipeline {
    agent any

    environment {
        // Name of the SonarQube server configured in Jenkins
        SONAR_SERVER = 'SonarQube'
        // Name of the SonarQube Scanner tool configured in Jenkins
        SONAR_SCANNER = 'SonarQubeScanner'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub...'
                checkout scm
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    // This loads the tool you configured in Global Tool Configuration
                    def scannerHome = tool name: "${SONAR_SCANNER}"
                    
                    withSonarQubeEnv("${SONAR_SERVER}") {
                        // Executes the scanner using the installed tool's path
                        sh "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }

        stage('Build') {
            steps {
                echo 'Building Scouter application...'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }
    }
}