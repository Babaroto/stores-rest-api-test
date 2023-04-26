pipeline {
    agent any

    stages {
        stage('Setup') {
            steps {
                sh 'python3.11 -m venv venv'
                sh 'source venv/bin/activate'
                sh 'pip install pytest'
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run tests') {
            steps {
                sh '. venv/bin/activate'
                sh 'pytest test/'
            }
        }
    }
}