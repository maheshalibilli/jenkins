pipeline {
    agent any
    environment {
        VENV = 'venv'
    }
    stages {
        stage('Checkout git') {
            steps {
                git branch: 'main', url: 'https://github.com/Parth2k3/test-flask'
            }
        }
        stage('Set up the venv') {
            steps {
                sh '''
                    python3 -m venv ${VENV}
                    . ${VENV}/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }
        stage('RUN THE TESTS') {
            steps {
                sh '''
                    . ${VENV}/bin/activate
                    python -m unittest discover -s tests
                '''
            }
        }
    }
}
