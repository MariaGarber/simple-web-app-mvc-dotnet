pipeline {
    agent none

    stages {
        stage('Build') {
            agent {
                label 'docker'
            }
            steps {
                container('dotnet') {
                    sh 'dotnet build'
                }
            }
        }

        stage('Publish') {
            agent {
                label 'docker'
            }
            steps {
                container('dotnet') {
                    sh 'dotnet publish -o ./publish'
                }
            }
        }

        stage('Upload') {
            agent {
                label 'docker'
            }
            steps {
                container('kubectl') {
                    sh 'kubectl cp ./publish web-app:/var/web-app -n default'
                }
            }
        }
    }

    // Define the pod template for running containers
    options {
        podTemplate {
            containers {
                container('dotnet') {
                    image 'dotnet'
                    ttyEnabled true
                }
                container('kubectl') {
                    image 'kubectl'
                    ttyEnabled true
                }
            }
        }
    }
}
