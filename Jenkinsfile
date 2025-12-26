pipeline {
    agent any
    
    tools {
        nodejs 'NodeJS'  // Make sure NodeJS is configured in Jenkins Global Tool Configuration
    }
    
    environment {
        // Define environment variables
        NODE_ENV = 'development'
    }
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }
        
        // stage('Lint') {
        //     steps {
        //         echo 'Running linting...'
        //         sh 'npm run lint || true'  // Continue even if linting fails
        //     }
        // }
        
        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'pwd'
                sh 'ls -la'
                sh 'ls node_modules/.bin || true'
                sh 'npm -v'
                sh 'node -v'
                sh 'npm install'
                sh 'npm run build'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
                // Add test command when tests are configured
                sh 'echo "No tests configured yet"'
            }
        }
        
        stage('Archive Artifacts') {
            steps {
                echo 'Archiving build artifacts...'
                archiveArtifacts artifacts: 'dist/**/*', fingerprint: true
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                // Add your deployment steps here
                // For example: copying to web server, uploading to S3, etc.
                sh 'echo "Deployment step - configure as needed"'
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
        always {
            echo 'Cleaning up workspace...'
            cleanWs()
        }
    }
}
