pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Stage 1: Building the code using Maven'
                // Tool: Maven
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Running unit and integration tests using JUnit'
                // Tool: JUnit (for unit tests), Selenium (for integration tests)
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Running code analysis using SonarQube'
                // Tool: SonarQube
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Stage 4: Running security scan using OWASP Dependency Check'
                // Tool: OWASP Dependency Check
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploying to a staging environment (e.g., AWS EC2)'
                // Deployment tool could be AWS CLI or Terraform
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Running integration tests on staging using Selenium'
                // Tool: Selenium
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploying to production environment (e.g., AWS EC2)'
                // Deployment tool could be AWS CLI or Terraform
            }
        }
    }
    post {
        success {
            echo 'Pipeline completed successfully'
            mail to: 'oshan3929@gmail.com',
                 subject: "Pipeline Success",
                 body: "The pipeline completed successfully."
        }
        failure {
            echo 'Pipeline failed'
            mail to: 'oshan3929@gmail.com',
                 subject: "Pipeline Failed",
                 body: "The pipeline failed."
        }
    }
}
