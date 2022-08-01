pipeline {
    agent any
    tools {
        maven 'maven'
    }

    stages {
        stage('Checkout and Compile') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Unit Tests') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Static Code analysis') {
            steps {
                echo 'Code analysis....'
            }
        }
        stage('Package') {
            steps {
                echo 'Package....'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}