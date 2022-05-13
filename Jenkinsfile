pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                git url: 'git@github.com:Rodrigomontenegrofarias/pipeline.git', branch: 'main',
                credentialsId:'github_creds'
                
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh('git remote -v')
                sh('git show-ref')
                sh('git config --global user.email "rodrigo.montenegro@alumnos.uv.cl"')
                sh('git config --global user.name "Rodrigomontenegrofarias"')
                sh('git tag $BUILD_NUMBER -a -m "git commit $BUILD_NUMBER"')
                sh('git push --tags')
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}