pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                git url: 'https://github.com/Rodrigomontenegrofarias/pipeline', branch: 'main',
                credentialsId:'github_creds'
                sh('git remote -v')
                sh('git show-ref')
                sh('git config --global user.email "rodrigo.montenegro@alumnos.uv.cl"')
                sh('git config --global user.name "Rodrigomontenegrofarias"')
                sh('git tag $BUILD_NUMBER -a -m "git commit $BUILD_NUMBER"')
                sh('git push origin --tags')

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