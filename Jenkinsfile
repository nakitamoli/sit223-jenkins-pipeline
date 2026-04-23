pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo '========== Stage 1: Build =========='
                echo 'Task: Compiling and packaging the application source code.'
                echo 'Tool: Maven'
                echo 'Command that would be run: mvn clean package'
                echo 'Build complete. Artifact generated at target/app.jar'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo '========== Stage 2: Unit and Integration Tests =========='
                echo 'Task: Running unit tests to verify individual components function correctly.'
                echo 'Task: Running integration tests to verify components work together as expected.'
                echo 'Tools: JUnit (unit tests), TestNG (integration tests)'
                echo 'Commands that would be run: mvn test, mvn verify'
                echo 'All unit and integration tests passed successfully.'
            }
        }

        stage('Code Analysis') {
            steps {
                echo '========== Stage 3: Code Analysis =========='
                echo 'Task: Analysing source code for quality issues, code smells, and adherence to industry standards.'
                echo 'Tool: SonarQube'
                echo 'Command that would be run: mvn sonar:sonar'
                echo 'Code analysis complete. No critical issues found.'
            }
        }

        stage('Security Scan') {
            steps {
                echo '========== Stage 4: Security Scan =========='
                echo 'Task: Scanning the application and dependencies for known security vulnerabilities and CVEs.'
                echo 'Tool: OWASP Dependency-Check'
                echo 'Command that would be run: dependency-check --scan ./ --format HTML'
                echo 'Security scan complete. No critical vulnerabilities detected.'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo '========== Stage 5: Deploy to Staging =========='
                echo 'Task: Deploying the packaged application to the staging server for pre-production testing.'
                echo 'Environment: AWS EC2 instance (Staging)'
                echo 'Tool: AWS CLI / SCP'
                echo 'Command that would be run: scp target/app.jar ec2-user@staging-server:/app/'
                echo 'Application successfully deployed to staging environment.'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo '========== Stage 6: Integration Tests on Staging =========='
                echo 'Task: Running integration tests against the live staging environment to simulate production conditions.'
                echo 'Tool: Selenium / Postman (Newman CLI)'
                echo 'Command that would be run: newman run staging-tests.json --environment staging-env.json'
                echo 'All staging integration tests passed. Application behaves as expected.'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo '========== Stage 7: Deploy to Production =========='
                echo 'Task: Deploying the verified application build to the live production server.'
                echo 'Environment: AWS EC2 instance (Production)'
                echo 'Tool: AWS CLI / SCP'
                echo 'Command that would be run: scp target/app.jar ec2-user@production-server:/app/'
                echo 'Application successfully deployed to production environment.'
            }
        }

    }

    post {
        success {
            echo 'Pipeline completed successfully. All stages passed.'
        }
        failure {
            echo 'Pipeline failed. Please review the logs above.'
        }
    }
}
