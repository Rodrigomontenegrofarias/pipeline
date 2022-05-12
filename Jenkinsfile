pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                git url: 'https://github.com/Rodrigomontenegrofarias/pipeline', branch: 'main',
                credentialsId:'github_creds'
            }

        }
        stage('Checkout') {
            steps {
              checkout scm: [$class: 'GitSCM', userRemoteConfigs: [[url: 'https://github.com/Rodrigomontenegrofarias/pipeline', credentialsId: 'github_creds' ]], branches: [[name: 'main/${TAG}']]], poll: false
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}