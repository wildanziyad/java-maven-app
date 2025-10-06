pipeline {
    agent any

    tools {
        maven 'maven-3.9'
    }

    stages {
        stage('Build Jar') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Build Image') {
            steps {
                script {
                    echo 'Building the Docker image...'
                    withCredentials([string(credentialsId: 'docker-hub-credential', variable: 'PASSWORD')]) {
                        sh '''
                        echo $PASSWORD | docker login -u dockerhub-user --password-stdin
                        docker build -t your-dockerhub-username/your-image:tag .
                        docker push your-dockerhub-username/your-image:tag
                        '''
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
            }
        }
    }
}
