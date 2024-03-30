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
        
        stage('Despliegue en Entorno de Pruebas') {
            steps {
                // Agrega los pasos necesarios para implementar en un entorno de pruebas
                // Aquí se crea una imagen Docker y se ejecuta un contenedor de prueba
                sh 'docker build -t hello-devops .'
                sh 'docker run -d --name hello-devops-container hello-devops'
            }
        }
    }

    // Configuración para que Jenkins inicie automáticamente la construcción
    triggers {
        // Desencadena la construcción cuando se detectan cambios en el repositorio
        pollSCM('* * * * *')
    }

    // Configuración básica de notificaciones
    post {
        success {
            // Notificar por correo electrónico si la construcción es exitosa
            emailext body: 'La construcción se ha completado con éxito.',
                     subject: 'Construcción Exitosa',
                     to: 'tu_correo@example.com'
        }
        failure {
            // Notificar por correo electrónico si la construcción falla
            emailext body: 'La construcción ha fallado.',
                     subject: 'Error en la Construcción',
                     to: 'tu_correo@example.com'
        }
    }
}
