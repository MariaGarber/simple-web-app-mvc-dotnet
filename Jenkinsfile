pipeline {
    agent any

    stages {
        stage('Try'){
            steps {
                docker.image('ubuntu1804').withRun('-d=true -p 8888:8080') {c -> docker.image('ubuntu1804').inside{sh "ls"}}
            }
        }
        
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
