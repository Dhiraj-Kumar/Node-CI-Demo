pipeline {
    agent any

    tools {
        nodejs 'NodeJS'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Dhiraj-Kumar/Node-CI-Demo.git', branch: 'master'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Test') {
            steps {
                bat 'npm run test'
            }
        }

        stage('Publish') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    bat """
                    echo Building Docker image...
                    docker build -t dhiraj2001/myapp .

                    echo Logging into Docker Hub...
                    docker login -u %DOCKER_USER% -p %DOCKER_PASS%

                    echo Pushing Docker image...
                    docker push dhiraj2001/myapp

                    echo Logging out...
                    docker logout
                    """
                }
            }
        }
    }
}
