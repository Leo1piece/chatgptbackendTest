pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                //all branch tigger jenkins，需要加multibranch
                git branch: '*', credentialsId: 'chatgptbackend', url: 'https://github.com/Leo1piece/chatgptbackendTest.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
