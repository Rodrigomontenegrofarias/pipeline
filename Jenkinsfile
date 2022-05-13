pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                git url: 'https://github.com/Rodrigomontenegrofarias/pipeline.git', branch: 'main',
                credentialsId:'github_creds'
                
            }
        }

       // stage('Test') {
       //     steps {
       //         echo 'Testing..'
       //         sh('git remote -v')
       //         sh('git config --global user.email "rodrigo.montenegro@alumnos.uv.cl"')
       //         sh('git config --global user.name "Rodrigomontenegrofarias"')
       //         sh('git tag $BUILD_NUMBER -a -m "git commit $BUILD_NUMBER"')
       //         sh('cat -/.gitconfig')
       //         sh('git push --tags')
       //     }
       // }

        stage('Deploy') {
            steps {
                echo 'Deploying....'
                withCredentials([usernamePassword(credentialsId: 'github_creds',
                passwordVariable: 'Rodrigojesus1001', usernameVariable: 'Rodrigomontenegrofarias')]) {

                sh('git tag -a $BRANCH_NAME.$BUILD_NUMBER -m "git sha is $GIT_COMMIT"')

                sh('git push https://$GIT_USER:$GIT_...@github.com/Rodrigomontenegrofarias/pipeline.git' --tags')
                }
            }
        }
    }
}