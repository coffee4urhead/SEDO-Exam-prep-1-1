pipeline {
    agent any
    stages {
        stage('Restore Dependencies') {
            when {
                anyOf {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps {
                cbat 'dotnet restore'
            }
        }
        stage('Build the app') {
                        when {
                anyOf {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps {
                cbat 'dotnet restore'
            }
            steps {
                bat 'dotnet build --norestore'
            }
        }
        stage('Run Tests') {
                        when {
                anyOf {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps {
                cbat 'dotnet restore'
            }
            steps {
                bat 'dotnet test'
            }
        }
    }

    post {
        success {
            echo "Build succeeded: ${env.BUILD_URL}"
        }
        failure {
            echo "Build failed: ${env.BUILD_URL}"
        }
    }
}