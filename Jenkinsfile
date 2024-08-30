

pipeline {
    agent any

    environment
    {
        DIRECTORY_PATH = "${env.WORKSPACE}"
        TESTING_ENVIRONMENT = 'TestingEnvironment'
        PRODUCTION_ENVIRONMENT = 'Chalani Lamahewa'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                echo 'Build automation tool : Maven'
                echo 'mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests...'
                echo 'Test automation tool : Maven Surefire Plugin for integration tests'
                echo 'mvn test'
            }
            post {
                always {     mail to: 'chalalamahewa@gmail.com',
                             subject: "Unit and Integration Test Result: ${currentBuild.currentResult}",
                             body: "The unit and integration test stage has completed with status: ${currentBuild.currentResult}.",

                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing Code Analysis...'
                echo 'Code analysis tool : SonarQube'
                echo 'mvn sonar:sonar'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan...'
                // Security scanning tool
                echo 'Security scanning tool'
                echo 'mvn dependency-check:check'
            }
            post {
                always {
                             mail to: 'chalalamahewa@gmail.com',
                             subject: "Security Scan Result: ${currentBuild.currentResult}",
                             body: "The security scan stage has completed with status: ${currentBuild.currentResult}.",

                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
                // Deploy to staging server, e.g., using SSH or AWS CLI for EC2 instances
                echo 'Tool: SSH'
                echo 'Task: Deploy the application to a staging server AWS EC2 using SSH '
            
            }
        }


        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging...'
                echo 'Tool: Maven with staging profile'
                echo 'Task: Run integration tests on the staging environment to ensure the application functions as expected.'
                
            }
            post {
                always {
                             mail to: 'chalalamahewa@gmail.com',
                             subject: "Integration Test on Staging Result: ${currentBuild.currentResult}",
                             body: "The integration tests on staging stage have completed with status: ${currentBuild.currentResult}.",

                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                echo 'Tool: SSH'
                echo 'Task: Deploy the application to a production server AWS EC2 using SSH.'
        }
        }
    }

    post {
        always {
            echo 'Pipeline finished'
        }
    }
}
