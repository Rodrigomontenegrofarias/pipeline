pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                git url: 'https://github.com/Rodrigomontenegrofarias/pipeline.git', branch: 'main',
                credentialsId:'github_creds'
                
                sh('git remote -v')
                sh('git config --global user.email "rodrigo.montenegro@alumnos.uv.cl"')
                sh('git config --global user.name "Rodrigomontenegrofarias"')
                sh('git tag $BUILD_NUMBER -a -m "git commit $BUILD_NUMBER"')         
                sh('git push')
                //sh('cat -/.gitconfig')
                
               // sh(' git clone https://github.com/Rodrigomontenegrofarias/pipeline.git')
            }
        }

        stage('Test') {
            steps {
                echo 'Testing..'
                
            }
        }        
    }
}