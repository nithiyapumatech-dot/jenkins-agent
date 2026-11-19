pipeline {
    agent {
        label 'windows-agent'
    }

    stages {

        stage('Build') {
            steps {
                echo 'Building application'

                bat 'echo Build Successful > build.txt'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing application'

                bat '''
                if exist build.txt (
                    echo Test Passed
                ) else (
                    echo Test Failed
                    exit /b 1
                )
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application'

                bat '''
                if not exist deploy mkdir deploy
                copy build.txt deploy\\build.txt
                dir deploy
                '''
            }
        }
    }
}
