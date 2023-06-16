pipeline {
    agent any

    stages {
        stage('Compile .NET Core Application') {
            agent {
                kubernetes {
                    namespace 'devops'
                }
            }

            steps {
                container('dotnet') {
                    sh 'dotnet build'
                }
            }
        }

        stage('Upload Application') {
            agent {
                kubernetes {
                    namespace 'maria'
                }
            }

            steps {
                container('kubectl') {
                    sh 'kubectl apply -f deployment.yaml'
                }
            }
        }
    }
}
