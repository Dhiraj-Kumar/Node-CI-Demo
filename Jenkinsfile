pipeline {
    stages {
        stage('Clone') {
            steps {
                git branch: 'master', url: 'https://github.com/Dhiraj-Kumar/Node-CI-Demo.git'        }
        }
        stage('Build') {
            steps {
                sh 'npm install'        }
        }
        stage('Test') {
            steps {
                sh 'npm run test'        }
        }
    }
}