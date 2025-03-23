pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout([$class: 'GitSCM', 
                        branches: [[name: '*/main']], 
                        userRemoteConfigs: [[
                            url: 'https://github.com/Marshini-Gunasekar/Jenkins-repo.git',
                            credentialsId: 'your-jenkins-git-credentials'
                        ]]
                    ])
                }
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Building Project..."'
            }
        }

        stage('Test') {
            steps {
                sh 'echo "Running Tests..."'
            }
        }

        stage('Deploy') {
            steps {
                sh 'echo "Deploying Application..."'
            }
        }
    }
}
