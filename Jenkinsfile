pipeline {
    agent any

    stages {
        stage('inicializar') {
            steps {
                sh "git clone "
            }
        }
        stage('Build') {
            steps {                
                    sh "docker build -t app"
                } 
        }
        stage('Deploy on develop.') {
            when { 
                BRANCH_NAME == develop 
            }
            steps {
                sh "kubectl apply -f deployment"
                echo 'Deploying....'
            }
        }
        stage('Deploy on stagging.') {
            when { 
                BRANCH_NAME == stagging 
            }
            steps {
                sh "kubectl apply -f deployment"
                echo 'Deploying....'
            }
        }
        stage('Deploy on production') {
            when { 
                BRANCH_NAME == master 
            }
            steps {
                sh "kubectl apply -f deployment"
                echo 'Deploying....'
            }.
        }
    }
}