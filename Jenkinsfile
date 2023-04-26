pipeline{
    agent any
    stages {
        stage('Setup'){
            steps{
                sh 'python3.11 -m venv venv'
                sh 'source venv/bin/activate'
                sh 'pip install pytest'
                sh 'pip install -r /ruta/completa/requirements.txt'
            }
        }
        stage('Run test'){
            steps{
                script {
                    withPythonEnv('venv') {
                        sh 'pytest test/'
                    }
                }
            }
        }
    }
}