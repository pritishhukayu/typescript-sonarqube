pipeline {
    agent any // You can specify a specific agent label here if needed

    stages {
        stage('SCM') {
            steps {
                checkout scm
            }
        }
        
        stage('SonarQube Analysis') {
            environment {
                // Define SONAR_RUNNER_HOME environment variable to point to the SonarScanner tool
                SONAR_RUNNER_HOME = tool 'SonarScanner'
            }
            steps {
                script {
                    // Execute SonarScanner using the defined SONAR_RUNNER_HOME
                    sh "${SONAR_RUNNER_HOME}/bin/sonar-scanner"
                }
            }
        }
    }
    
    // Optionally, you can add post-build actions or notifications here
    // post {
    //     success {
    //         // Add success post-build actions
    //     }
    //     failure {
    //         // Add failure post-build actions
    //     }
    // }
}
