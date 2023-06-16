pipeline {
    agent none

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'dotnet'
                    label 'docker'
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
                    label 'docker'
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
                    label 'docker'
                }
            }
            steps {
                sh 'kubectl cp ./publish web-app:/var/web-app -n default'
            }
        }
    }
}
