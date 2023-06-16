pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'dotnet'
                }
            }
            steps {
                sh 'dotnet build'
            }
        }

        stage('Publish') {
            agent {
                docker {
                    image 'dotnet'
                }
            }
            steps {
                sh 'dotnet publish -o ./publish'
            }
        }

        stage('Upload') {
            agent {
                docker {
                    image 'kubectl'
                }
            }
            steps {
                sh 'kubectl cp ./publish web-app:/var/web-app -n default'
            }
        }
    }
}
