pipeline {
    agent any

    environment {
        APP_NAME   = 'hello-pipeline'
        DEPLOY_DIR = '/tmp/deploy/hello-pipeline'
    }

    options {
        timeout(time: 10, unit: 'MINUTES')
        timestamps()
    }

    stages {
        stage('Build') {
            steps {
                sh 'python3 -m venv venv'
                sh '. venv/bin/activate && pip install -r requirements.txt'
            }
        }
        stage('Test') {
            steps {
                sh '. venv/bin/activate && pytest --junitxml=results.xml'
            }

