pipeline {
    agent any

    stages { 
        stage('Checkout'){
            steps {
                git branch: 'master', url: 'https://github.com/lula12devops/static-website-cicd.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t static-website-cicd:latest .'
            }
        }


        stage('Deploy Website') {
            steps {
                sh '''
                docker rm -f static-website-cicd || true
                docker run -d -p 80:80 --name static-website-cicd static-website-cicd:latest
                '''
            }
        }
    }
}
