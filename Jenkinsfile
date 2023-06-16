pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                container('dotnet') {
                    sh 'dotnet build'
                }
            }
        }
        
        stage('Publish') {
            steps {
                container('dotnet') {
                    sh 'dotnet publish -o ./publish'
                }
            }
        }
        
        stage('Upload') {
            steps {
                container('kubectl') {
                    sh 'kubectl cp ./publish web-app:/var/web-app -n default'
                }
            }
        }
    }
}
