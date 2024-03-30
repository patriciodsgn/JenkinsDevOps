pipeline {
    agent any
    
    stages {
        stage('Clonar Repositorio') {
            steps {
                // Clonar el repositorio de Git
                git 'https://github.com/patriciodsgn/HelloDevOps.git'
            }
        }
        
        stage('Construir') {
            steps {
                // Compilar la aplicación Java
                sh 'javac HelloWorld.java'
            }
        }
        
        stage('Pruebas') {
            steps {
                // Ejecutar pruebas unitarias
                sh 'java HelloWorld'
            }
        }
    }
}
