pipeline {
    agent any
    
    triggers {
        pollSCM('* * * * *') // Poll the repository every minute
    }
    stages {
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
                sh """
                echo "Cleaned Up Workspace For Project"
                """
            }
        }
        stage('Code Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM', 
                    branches: [[name: '*/main']], 
                    userRemoteConfigs: [[url: 'https://github.com/yrprasadgem/declyaml.git']]
                ])
            }
        }
        stage(' Unit Testing') {
            steps {
                sh """
                echo "Running Unit Tests"
                """
            }
        }
        stage('Code Analysis') {
            steps {
                sh """
                echo "Running Code Analysis"
                """
            }
        }
        stage('Build Deploy Code') {
            steps {
                sh """
                echo "Building Artifact"
                """
                sh """
                echo "Deploying Code"
                """
            }
        }
        stage('Deploy to Production') {
            steps {
                input(message: 'Deploy to production?', ok: 'Deploy')                
                // Deployment steps to the production environment 
                // changed the comment observe it should trigger in a minute
            }
        }
    }
}
