pipeline {

    agent any

    stages {

        stage('Install Dependencies') {
            steps {
                echo 'Static HTML project - no dependencies required'
            }
        }


        stage('Run Tests') {
            steps {
                bat 'if exist index.html (echo index.html found) else (exit 1)'
            }
        }


        stage('Build') {
            steps {
                echo 'Preparing static website files'
                bat 'dir'
            }
        }


        stage('Deploy to EC2') {
            steps {
                sshPublisher(
                    publishers: [
                        sshPublisherDesc(
                            configName: 'aws-ec2',
                            transfers: [
                                sshTransfer(
                                    sourceFiles: 'index.html',
                                    remoteDirectory: '/var/www/html'
                                )
                            ],
                            verbose: true
                        )
                    ]
                )
            }
        }
    }


    post {
        success {
            echo 'Deployment completed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }
    }
}