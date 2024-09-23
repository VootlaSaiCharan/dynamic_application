pipeline {
    agent any
    parameters {
        choice choices: ['create', 'delete'], description: 'creating and deleting', name: 'action'
    }

    stages {
        stage('Build') {
            when { expression { return params.action == 'create'}}
            steps {
                git branch: 'parameter', url: 'https://github.com/VootlaSaiCharan/dynamic_application.git'
            }
        }
        stage('Run Docker Compose') {
            when { expression { return params.action == 'create'}}
            steps {
                script{
                    sh 'docker-compose up -d'
                }
            }
        }
        stage('Delete Docker Compose') {
            when { expression { return params.action == 'delete'}}
            steps {
                script{
                    sh 'docker-compose down'
                }
            }
        }
    }
}