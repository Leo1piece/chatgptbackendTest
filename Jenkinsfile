pipeline {
    agent any

    stages {
        stage('Git checkout') {
            steps{
                // Get source code from a GitHub repository
                git branch:'main', url:'https://github.com/Leo1piece/chatgptbackendTest.git'
            }
        }
        
        stage('npm install') {
            steps{
                dir("./apis/userprofile/") {
                    sh 'npm install'
                }
            }
        }
        
        stage('Tests') {
            steps{
                dir("./apis/userprofile/") {
                    sh 'npm test'
                }
            }
        }
        
        stage('npm coverage') {
            steps{
                dir("./apis/userprofile/") {
                    sh 'npm run cover'
                }
            }
        }

        stage('Publish') {
            steps{
                sh 'ls -la ./apis/userprofile/'
            }
        }
    }
}
