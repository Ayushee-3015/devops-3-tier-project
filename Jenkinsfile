pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-flask-app:latest ./app'
            }
        }

        stage('Test Application') {
    steps {
        sh '''
            docker rm -f devops-test >/dev/null 2>&1 || true
            docker run -d --name devops-test -p 5001:5000 devops-flask-app:latest
            sleep 5
            curl -f http://host.docker.internal:5001/health
            docker rm -f devops-test
        '''
    }
}

        stage('Deploy to Kubernetes') {
            steps {
                echo 'Kubernetes deployment stage'
                echo 'Application is ready for Kubernetes deployment'
            }
        }
    }
}
