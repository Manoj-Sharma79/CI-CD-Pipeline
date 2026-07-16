pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/Manoj-Sharma79/CI-CD-Pipeline'
            }
        }

        stage('Build') {
            steps {
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip install --upgrade pip
                pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                . venv/bin/activate
                pytest
                '''
            }
        }

        stage ('Deploy') {
            steps {
                sh '''
                pkill -f app.py || true
                nohup python3 app.py > flask.log 2>&1 &
                '''
            }
        }

    }

}