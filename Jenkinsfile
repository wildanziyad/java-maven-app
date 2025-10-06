pipeline {
    agent any
    tools {
        maven 'maven-app'
    }

    stages {
        stage('Test') {
            steps {
                echo "Testing the application..."
                echo "Executing pipeline for branch ${env.BRANCH_NAME}"
            }
        }

        stage('Build') {
            when {
                expression { env.BRANCH_NAME == 'main' }
            }
            steps {
                sh 'mvn clean package'
                echo "Building the application..."
            }
        }

        stage('Deploy') {
            when {
                expression { env.BRANCH_NAME == 'main' }
            }
            steps {
                echo "Deploying the application..."
            }
        }
    }
}
