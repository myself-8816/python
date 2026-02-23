pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                echo "Using local workspace code"
            }
        }

        stage('Install Dependencies') {
            steps {
                echo "Installing dependencies..."
                sh 'pip3 install -r requirements.txt || true'
            }
        }

        stage('Build') {
            steps {
                echo "Running Python build..."
                sh 'python3 app.py'
            }
        }

        stage('Package') {
            steps {
                echo "Creating package..."
                sh 'tar -czf python-build-demo.tar.gz .'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: '*.tar.gz', fingerprint: true
            }
        }

    }
}
