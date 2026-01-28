pipeline {
    agent any

    stages {
        stage("Check Docker version") {
            steps {
                sh "docker --version"
            }
        }
        stage("Verify") {
            steps {
                sh "dir"
            }
        }

        stage('Build Docker Image') { 
            steps { 
                sh 'docker build -t kwongheng/github-demo .' 
            } 
        }

        stage('Push Docker Image') { 
            steps { 
                withCredentials([usernamePassword(credentialsId: 'docker-hub credentials', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) { 
                    sh 'docker login -u %DOCKER_USERNAME% -p %DOCKER_PASSWORD%' 
                    sh 'docker push kwongheng/github-demo' 
                } 
            } 
        }
    }
}
