pipeline{
    agent any
    stages{
        stage('Source code repository') {
            steps{
                git branch: 'master', 
                url: 'https://github.com/vinodk090/devops-python.git'
            }
        }
        stage('Building Docker image') {
            steps{
                sh """
                docker build -t flask-app .
                docker tag flask-app:latest vinodk090/flask-app:latest
                """
            }
        }
        stage('Logging to docker hub') {
            steps{
                script {
                    withCredentials([usernamePassword(credentialsId: 'Docker-creds',
                                                     usernameVariable: 'DOCKER_USER',
                                                     passwordVariable: 'DOCKER_PASS')]) {
                        sh """
                        echo "Logging in to Docker Hub..."
                        echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin
                        """
                    }
            }
        }
        stage('Pushing Image to remote repository') {
            steps{
                script {
                    sh """
                    echo "Pushing Docker image to Docker Hub..."
                    docker push vinodk090/flask-app
                    """
                }
            }
        }
    }
}