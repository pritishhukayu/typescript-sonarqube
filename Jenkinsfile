pipeline {
    agent any

    stages {
        stage('SonarQube Analysis') {
            steps {
                script {
                    // Print environment variables
                    echo "PATH: ${env.PATH}"
                    echo "JAVA_HOME: ${env.JAVA_HOME}"
                    echo "M2_HOME: ${env.M2_HOME}"
                    
                    // Perform SonarQube analysis using SonarScanner
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
