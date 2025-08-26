pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo "Cloning the repository..."
                git branch: 'main', credentialsId: 'github-id', url: 'https://github.com/sheikshafeer/my-jenkins-project.git'
                sh "ls -ltr"
            }
        }

        stage('Setup Python Environment') {
            steps {
                echo "Setting up Python virtual environment..."
                sh '''
                    python3 -m venv venv
                    source venv/bin/activate
                    if [ -f requirements.txt ]; then
                        pip install --upgrade pip
                        pip install -r requirements.txt
                    else
                        echo "requirements.txt not found, skipping pip install."
                    fi
                '''
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully!"
        }
        failure {
            echo "Pipeline failed. Check logs for errors."
        }
    }
}

