pipeline {
    agent any

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
                // contoh build pakai maven langsung kalau mau:
                // sh 'mvn clean package'
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
