pipeline {
    agent any

    stages {
        stage('Version'){
            steps{
            echo 'Revisando la version de python'
            sh 'python --version'
            echo 'Terminando la revision de python'
            }
        }

        stage('Setup') {
            steps {
                echo 'Creando entorno virtual de python3'
                sh 'pip install virtualenv'
                sh 'python3.11 -m venv venv'
                echo 'Instalando Dependencias'
                sh 'source venv/bin/activate'
                sh 'pip install pytest'
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run tests') {
            steps {
                echo 'Activando entorno virtual'
                sh 'source venv/bin/activate'
                echo 'Ejecutando pruebas'
                sh 'pytest test/'
            }
        }
    }
}