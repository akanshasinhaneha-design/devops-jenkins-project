pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/akanshasinhaneha-design/devops-jenkins-project.git'
            }
        }

        stage('Setup Python Env') {
            steps {
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh '''
                    . venv/bin/activate
                    python3 -m unittest discover -s .
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo "🎉 Deployment stage executed!"
            }
        }
    }

    post {
        always {
            echo "Pipeline complete."
        }
        success {
            echo "Build SUCCESS!"
        }
        failure {
            echo "Build FAILED!"
        }
    }
}
