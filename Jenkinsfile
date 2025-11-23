pipeline {
    agent any
    
    // Définit les outils (à configurer dans Jenkins plus tard)
    tools {
        jdk 'JAVA_HOME'
        maven 'M3' 
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
                sh 'mvn clean compile'
            }
        }
        
        stage('Tests') {
            steps {
                sh 'mvn test -Dmaven.test.skip=false'
            }
        }
        
        stage('Packaging') {
            steps {
                sh 'mvn clean install -Dmaven.test.skip=true'
            }
        }
    }
    
    post {
        success {
            echo "Build réussi ! Le JAR est généré."
        }
        failure {
            echo "Échec du build."
        }
    }
}
