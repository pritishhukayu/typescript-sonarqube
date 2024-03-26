pipeline {
    agent any

    stages {
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
}
