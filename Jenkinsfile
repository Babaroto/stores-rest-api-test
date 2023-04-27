pipeline {
    agent any

    stages {

        stage('Checkout'){
            steps{
            echo "Iniciando comprobaciones"
            checkout([$class: 'GitSCM', branches: [[name: 'master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Babaroto/stores-rest-api-test.git' ]]])
            echo "Terminando comprobaciones"
            }
        }

        stage('Version'){
            steps{
            echo 'Revisando la version de python'
            sh 'python3 --version'
            echo 'Terminando la revision de python'
            }
        }

        stage('Setup') {
            steps {
                echo 'Creando entorno virtual de python3'
                bat 'pip install virtualenv'
                bat 'python -m venv venv'
                echo 'Instalando Dependencias'
                bat 'venv\\Scripts\\activate.bat'
                bat 'pip install pytest'
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Run tests') {
            steps {
                echo 'Activando entorno virtual'
                bat 'venv\\Scripts\\activate.bat'
                echo 'Ejecutando pruebas'
                bat 'pytest test/'
            }
        }
    }
}