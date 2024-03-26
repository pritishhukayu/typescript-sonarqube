pipeline {
    agent any

    stages {
        stage('SonarQube Analysis') {
            steps {
                // Perform SonarQube analysis using SonarScanner
                script {
                    withSonarQubeEnv('SonarScanner') {
                        def scannerHome = tool 'SonarScanner'
                        echo "SonarScanner home: ${scannerHome}"
                        sh "ls -l ${scannerHome}/bin"
                        sh "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }
    }
}
