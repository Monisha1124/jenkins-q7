pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo '=== STAGE: CHECKOUT ==='
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo '=== STAGE: BUILD ==='
                echo 'Compiling app.py...'
                sh 'python3 -m py_compile app.py'
                
                echo 'Pausing build execution for 20 seconds...'
                sleep time: 20, unit: 'SECONDS'
                
                echo 'Passing milestone(1)...'
                milestone(1)
            }
        }

        stage('Deploy') {
            steps {
                echo '=== STAGE: DEPLOY ==='
                milestone(2)
                
                echo 'Executing deployment steps...'
                sh 'echo "DEPLOYMENT SUCCESSFUL: Application build has successfully deployed to production."'
            }
        }
    }
}