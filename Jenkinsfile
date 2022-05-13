pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                git url: 'https://github.com/Rodrigomontenegrofarias/pipeline.git', branch: 'main',
                credentialsId:'github_creds'
                sh('nano 1.py')
                sh('git add .')
                sh('git commit -m "aa1"')
                //sh('cat -/.gitconfig')
                
               // sh(' git clone https://github.com/Rodrigomontenegrofarias/pipeline.git')
            }
        }

       // stage('Test') {
       //     steps {
       //         echo 'Testing..'
       //         sh('git remote -v')
       //         sh('git config --global user.email "rodrigo.montenegro@alumnos.uv.cl"')
       //         sh('git config --global user.name "Rodrigomontenegrofarias"')
       //         sh('git tag $BUILD_NUMBER -a -m "git commit $BUILD_NUMBER"')
       //         
       //        sh('git push --tags')
       //     }
       // }

        stage('Deploy') {
            steps {
                echo 'Deploying....'
                withCredentials([usernamePassword(credentialsId: 'github_creds',
                passwordVariable: 'Rodrigojesus1001', usernameVariable: 'Rodrigomontenegrofarias')]) {
                sh('git tag $BUILD_NUMBER -a -m "git sha is $BUILD_NUMBER"')
                sh('git push --tags')
                }
           } 
        }
    }
}