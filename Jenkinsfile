pipeline {
    agent any
      tools {
            maven 'Maven 3'  // This matches the name you set in the global configuration
        }
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the repository
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    // Run Maven build to clean and package the application, skipping tests during build
                    echo 'Building the Spring Boot application...'
                    sh "${MAVEN_HOME}/bin/mvn clean package -DskipTests"
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run Maven tests
                    echo 'Running tests...'
                    sh "${MAVEN_HOME}/bin/mvn test"
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs for details.'
        }
        always {
            // Clean up or notify (optional)
            echo 'Pipeline execution completed.'
        }
    }
}