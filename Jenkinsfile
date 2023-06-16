pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code from the repository
                git 'https://github.com/MariaGarber/simple-web-app-mvc-dotnet'
            }
        }
        
        stage('Restore Packages') {
            steps {
                // Restore NuGet packages
                sh 'dotnet restore'
            }
        }
        
        stage('Build') {
            steps {
                // Build the .NET application using MSBuild
                sh 'dotnet build --configuration Release'
            }
        }
    }
}
