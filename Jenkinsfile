pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code...'
            }
        }

        stage('Deploy Dashboard') {
            steps {
                sh '''
                sudo cp index.html /var/www/html/
                sudo cp script.js /var/www/html/
                '''
            }
        }
    }
}
