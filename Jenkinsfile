pipeline {
    agent {
        docker {
            image 'your-docker-image-with-kubectl'
        }
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/your/repository.git'
            }
        }
        
        stage('Compile .NET Core Application') {
            steps {
                sh 'dotnet build'
            }
        }
        
        stage('Upload Application') {
            steps {
                sh 'kubectl apply -f deployment.yaml --namespace maria'
            }
        }
    }
}
