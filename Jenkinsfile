pipeline {
    agent any

    tools {
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }

    triggers {
        pollSCM('* * * * *') // Vérifie chaque minute
    }

    stages {
        stage('Clean Workspace') {
            steps {
                cleanWs()
            }
        }

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/imen-kh/DevOpsProjet.git'
            }
        }

        stage('Compilation') {
            steps {
                dir('StudentsManagement-DevOps-main') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage('Tests') {
            steps {
                dir('StudentsManagement-DevOps-main') {
                    sh 'mvn test -DskipTests=true'
                }
            }
        }

        stage('Packaging') {
            steps {
                dir('StudentsManagement-DevOps-main') {
                    sh 'mvn clean package -DskipTests'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
pipeline {
    agent any

    tools {
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }

    triggers {
        pollSCM('* * * * *') // Vérifie chaque minute
    }

    stages {
        stage('Clean Workspace') {
            steps {
                cleanWs()
            }
        }

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/imen-kh/DevOpsProjet.git'
            }
        }

        stage('Compilation') {
            steps {
                dir('StudentsManagement-DevOps-main') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage('Tests') {
            steps {
                dir('StudentsManagement-DevOps-main') {
                    sh 'mvn test -DskipTests=true'
                }
            }
        }

        stage('Packaging') {
            steps {
                dir('StudentsManagement-DevOps-main') {
                    sh 'mvn clean package -DskipTests'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("imen593/alpine:${env.BUILD_NUMBER}")
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-hub-credentials') {
                        dockerImage.push()
                        dockerImage.push('latest')
                    }
                }
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline terminé avec succès !"
        }
        failure {
            echo "❌ Échec du pipeline"
        }
    }
}                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-hub-credentials') {
                        dockerImage.push()
                        dockerImage.push('latest')
                    }
                }
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline terminé avec succès !"
        }
        failure {
            echo "❌ Échec du pipeline"
        }
    }
}
