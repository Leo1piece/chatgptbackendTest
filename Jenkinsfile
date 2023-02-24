pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                //all branch tigger jenkins，需要加multibranch
                git branch: '*', credentialsId: 'chatgptbackend', url: 'https://github.com/Leo1piece/chatgptbackendTest.git'
                echo 'checkout..'
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'cp .env.example .env'
                sh 'npm install'
                sh 'npm install eslint --save-dev'
                sh 'npm run build'
                sh 'pwd'
                sh 'ls -la'
                //sh 'docker build -t $registry/$image:$BUILD_NUMBER .'
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
