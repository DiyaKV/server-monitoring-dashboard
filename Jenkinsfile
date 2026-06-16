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
                sudo cp style.css /var/www/html/
                '''
            }
        }
    }

    post {
        success {
            emailext(
                subject: 'Jenkins Build Success',
                body: '''
Hello,

The latest deployment of the Server Monitoring Dashboard was SUCCESSFUL.

Job Name: ${JOB_NAME}
Build Number: ${BUILD_NUMBER}
Build URL: ${BUILD_URL}

Regards,
Jenkins
''',
                to: 'diyakoolothvinod@gmail.com'
            )
        }

        failure {
            emailext(
                subject: 'Jenkins Build Failed',
                body: '''
Hello,

The latest deployment of the Server Monitoring Dashboard has FAILED.

Job Name: ${JOB_NAME}
Build Number: ${BUILD_NUMBER}
Build URL: ${BUILD_URL}

Please check the Jenkins console output.

Regards,
Jenkins
''',
                to: 'diyakoolothvinod@gmail.com'
            )
        }
    }
}
