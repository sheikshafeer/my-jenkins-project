pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/sheikshafeer/my-jenkins-project.git', branch: 'main'
                sh "ls -ltr"
            }
        }

        stage('Setup') {
            steps {
                sh "pip install -r requirements.txt"
                sh "pytest"
                sh "whoami"
            }
        }
    }
}
