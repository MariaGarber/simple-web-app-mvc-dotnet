pipeline {
    agent {
        kubernetes {
            cloud 'kubernetes'
            label 'my-kubernetes-agent'
        }
    }

    stages {
        stage('Compile .NET Core Application') {
            steps {
                container('dotnet') {
                    sh 'dotnet build'
                }
            }
        }

        stage('Upload Application') {
            steps {
                container('kubectl') {
                    sh 'kubectl apply -f deployment.yaml'
                }
            }
        }
    }
}
