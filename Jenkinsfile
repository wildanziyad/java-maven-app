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
                echo "Building the application..."
                sh 'mvn clean package'
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
