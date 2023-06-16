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
                bat 'nuget restore'
            }
        }
        
        stage('Build') {
            steps {
                // Build the .NET application using MSBuild
                bat 'msbuild /t:Build /p:Configuration=Release'
            }
        }
    }
}
