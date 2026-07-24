pipeline {

    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/priyanshxp/cicd.git'
            }
        }


        stage('Check Files') {
            steps {
                sh 'ls -la'
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
                                    remoteDirectory: '/home/ubuntu'
                                )
                            ],
                            verbose: true
                        )
                    ]
                )
            }
        }
    }
}
