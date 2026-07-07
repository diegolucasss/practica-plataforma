pipeline {
    agent any

    tools {
        nodejs "Node22"
        dockerTool 'Dockertool' 
    }

    stages {
        stage('Construir Imagen Docker') {
            steps {
                sh '''
                # Al usar 'dockerTool', el comando 'docker' ya queda disponible en el PATH
                docker build -t hola-mundo-node:latest .
                '''
            }
        }

        stage('Ejecutar Contenedor Node.js') {
            steps {
                sh '''
                # Detenemos y removemos el contenedor si ya existe uno previo
                docker stop hola-mundo-node || true
                docker rm hola-mundo-node || true
                
                # Ejecutamos el nuevo contenedor
                docker run -d --name hola-mundo-node -p 3000:3000 hola-mundo-node:latest
                '''
            }
        }
    }
}