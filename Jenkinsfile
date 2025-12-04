pipeline {
    agent any

    environment {
        DOCKERHUB = credentials('DOCKERHUB')
    }

    stages {
        stage('Checkout & Build') {
            steps {
                git branch: 'main', url: 'https://github.com/imen-kh/DevOpsProjet.git'
                dir('StudentsManagement-DevOps-main') {
                    sh 'mvn clean install -DskipTests'
                }
            }
        }

        stage('Docker Build & Push') {
            steps {
                dir('StudentsManagement-DevOps-main') {
                    sh '''
                        echo "Login avec $DOCKERHUB_USR ..."
                        echo "$DOCKERHUB_PSW" | docker login -u "$DOCKERHUB_USR" --password-stdin

                        docker build -t imen593/devopsprojet:latest .
                        docker push imen593/devopsprojet:latest

                        echo "IMAGE PUBLIÉE → https://hub.docker.com/r/imen593/devopsprojet"
                    '''
                }
            }
        }
    }

    post {
        success {
            echo 'success'
        }
    }
}
