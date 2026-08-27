pipeline {
    agent any

    environment {
        // Name of the SonarQube server configured in Jenkins under:
        // Manage Jenkins -> System -> SonarQube servers
        SONAR_SERVER = 'SonarQube'
        // Name of the SonarQube Scanner tool configured under:
        // Manage Jenkins -> Global Tool Configuration -> SonarQube Scanner
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
        withSonarQubeEnv("${SONAR_SERVER}") {
            sh 'sonar-scanner'
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