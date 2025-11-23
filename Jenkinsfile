pipeline {
    agent any

    tools {
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }

    stages {
        stage('Récupération du code') {
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
    }
    
    post {
        success {
            echo "Pipeline terminé avec succès !"
        }
        failure {
            echo "Échec du pipeline"
        }
    }
}
