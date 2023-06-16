pipeline {
    agent {
        docker {
            image 'alpine/k8s:1.24.12'
        }
    }

    stages {
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
