pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                // Checkout the source code from the version control system (Git)
                checkout scm
            }
        }
        stage('Build') {
            steps {
                // Install dependencies and build the TypeScript project
                script {
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }
        stage('SonarQube Analysis') {
            steps {
                // Perform SonarQube analysis using SonarScanner
                script {
                    def scannerHome = tool 'SonarScanner'
                    withSonarQubeEnv() {
                        sh "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }
    }

    post {
        always {
            // Clean up any temporary files or resources here
        }
    }
}
