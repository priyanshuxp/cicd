pipeline {

    agent any

    stages {

        stage('Check Files') {
            steps {
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