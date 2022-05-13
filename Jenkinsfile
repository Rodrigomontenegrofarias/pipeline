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
        stage('Test') {
            steps {
                echo 'Testing..'
                sh('git remote -v')
                sh('git show-ref')
                sh('git tag -a main.$BUILD_NUMBER -m "git commit $BUILD_NUMBER"')
                sh('git push origin --tags')

            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}