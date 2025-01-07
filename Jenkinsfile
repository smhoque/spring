pipeline {
    agent any

    environment {
        // Set environment variables (you can customize these as needed)
        MAVEN_HOME = "C:\Users\emdadripon\Downloads\apache-maven-3.9.9-bin\apache-maven-3.9.9"
        JAVA_HOME = "C:\Program Files\Java\jdk-21"
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