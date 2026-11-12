
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/lohithareddygaali/external_com_5.git'
            }
        }

        stage('Compile') {
            steps {
                bat 'python -m py_compile app.py'
            }
        }

        stage('Test') {
            steps {
                bat 'python -m unittest app_test'
            }
        }

        stage('Package') {
            steps {
                bat 'tar -a -c -f PythonApp.zip app.py app_test.py'
            }
        }
    }

    post {
        success {
            echo 'Python CI/CD Pipeline Successful!'
            archiveArtifacts artifacts: 'PythonApp.zip'
        }

        failure {
            echo 'Pipeline Failed!'
        }
    }
}
