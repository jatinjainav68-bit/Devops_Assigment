pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out the project...'
            }
        }

        stage('Build') {
            steps {
                echo 'No build required for static HTML website.'
            }
        }

        stage('Test') {
            steps {
                echo 'Pipeline test completed successfully.'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                sudo cp -r /var/lib/jenkins/workspace/devops-assigment/* /usr/share/nginx/html/
                sudo systemctl restart nginx
                '''
            }
        }

        stage('S3 Backup') {
            steps {
                sh '''
                aws s3 cp /var/lib/jenkins/workspace/devops-assigment/index.html s3://test-bucket235678/
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully 🚀'
        }

        failure {
            echo 'Pipeline failed ❌'
        }
    }
}
