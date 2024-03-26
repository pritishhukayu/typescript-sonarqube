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
                    try {
                        sh 'npm install'
                        sh 'npm run build'
                    } catch (err) {
                        echo "Error occurred during build: ${err}"
                        currentBuild.result = 'FAILURE'
                        error("Build failed")
                    }
                }
            }
        }
        stage('SonarQube Analysis') {
            steps {
                // Perform SonarQube analysis using SonarScanner
                script {
                    withSonarQubeEnv('SonarQube') {
                        def scannerHome = tool 'SonarScanner'
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
        success {
            echo "Pipeline succeeded!"
        }
        failure {
            echo "Pipeline failed!"
        }
    }
}
