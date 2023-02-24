
pipeline {
    agent any

    environment {
        registry = "aws_account_id.dkr.ecr.us-east-1.amazonaws.com"
        image = "nodejs-app"
        awsregion = "us-east-1"
        app_name = "nodejs-app"
        cluster_name = "nodejs-cluster"
        service_name = "nodejs-service"
    }

    parameters {
        booleanParam defaultValue: true, description: 'Push to ECR', name: 'Push to ECR'
		}

    stages {

        stage('Checkout') {
            steps {
                //all branch tigger jenkins，需要加multibranch
               // git branch: '*', credentialsId: 'chatgptbackend', url: 'https://github.com/Leo1piece/chatgptbackendTest.git'
                git branch:'main', url:'https://github.com/Leo1piece/chatgptbackendTest.git'
            }
        }

        
        stage('Build') {
            steps {
                sh 'cp .env.example .env'
                sh 'npm install'
               // sh 'npm install eslint --save-dev'
                sh 'npm run start'
            
                //sh 'docker build -t $registry/$image:$BUILD_NUMBER .'
            }
        }

        stage('Test') {
            //
            steps { 
                //eslint 检查语法错误
                //sh 'npx eslint .'
                sh 'npm run test'
                sh 'pwd'
                sh 'ls -la'

            }
        }
/*
        stage('Push to ECR') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws-credentials', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
                    sh 'aws ecr get-login-password --region $awsregion | docker login --username AWS --password-stdin $registry'
                    sh "docker push $registry/$image:$BUILD_NUMBER"
                }
            }
        }

        stage('Deploy to ECS') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws-credentials', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
                    sh 'eval $(aws ecr get-login --region $awsregion --no-include-email)'
                    sh "sed -i 's|IMAGE|${registry}/${image}:${BUILD_NUMBER}|g' ecs-task-template.json"
                    sh "aws ecs create-cluster --cluster-name $cluster_name || true"
                    sh "aws ecs create-service --cluster $cluster_name --service-name $service_name --cli-input-json file://ecs-service-definition.json"
                }
            }
        }

*/
    }
}
