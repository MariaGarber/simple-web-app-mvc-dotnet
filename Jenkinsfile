pipeline {
    agent any
    
    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/MariaGarber/simple-web-app-mvc-dotnet'
            }
        }

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
