pipeline {
    agent any
    tools {
        maven 'mvn'
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                echo "${env.BUILD_NUMBER}"
                echo "${env.BUILD_URL}"
            }
        }
        stage('Code Quality analysis') {
            steps {
                echo 'Code analysis....'
            }
        }
        stage('Deploy to Dev') {
            steps {
                echo 'Deploying to Dev....'
            }
        }
        stage('Deploy to QA') {
            steps {
                echo 'Deploying to QA....'
            }
        }
        stage('Deploy to UAT') {
            steps {
                echo 'Deploying to UAT....'
            }
        }
        stage('Deploy to Per-prod') {
            steps {
                echo 'Staging....'
            }
        }
        stage('Prod Approval') {
            steps {
                script {
                    if(env.BRANCH_NAME == "master") {
                        input("Proceed Prod Deployment?")
                    }
                }
            }
        }
        stage('Deploy to Prod') {
            steps {
                echo 'Deploying....'
            }
            post {
                failure {
                    echo 'Production Build Failed'
                }
            }
        }
    }
    post {
        always {
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
        success {
             mail to: 'baddulurip@gmail.com',
             subject: "Build Succeded: ${currentBuild.fullDisplayName}",
             body: "Project build: ${env.JOB_NAME}"
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
             mail to: 'baddulurip@gmail.com',
             subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
             body: "Something is wrong with ${env.BUILD_URL}"
        }
        changed {
            echo 'Things were different before...'
        }
    }
}