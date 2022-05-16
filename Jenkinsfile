pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                git url: 'https://github.com/Rodrigomontenegrofarias/pipeline.git', branch: 'main',
                credentialsId:'github_creds'
                
                sh('git tag $BUILD_NUMBER -a -m "git commit $BUILD_NUMBER"')         
                sh('git remote remove origin')
                sh('git remote add origin https://Rodrigomontenegrofarias:Rodrigojesus1001@github.com/Rodrigomontenegrofarias/ci-cd-prueba.git')
                sh('ls -a')
                
            }
        }
        
        stage('Test') {
            steps {
                echo 'Testing..'
               // sh('git push --tags')
            //    sh('ssh-keygen -t ed25519 -C "rodrigo.montenegro@alumnos.uv.cl"')
            //    sh('cat /root/.ssh/id_rsa.pub')
            //    sh('cat /root/.ssh/id_rsa.pub')
                sh('git remote -v')
                sh('git config --global user.email "rodrigo.montenegro@alumnos.uv.cl"')
                sh('git config --global user.name "Rodrigomontenegrofarias"')
            }
        }
    ///    stage('scan') {
       //   environment {
            // Previously defined in the Jenkins "Global Tool Configuration"
        //    scannerHome = tool 'sonar-scanner'
          }
        //  steps {
            // "sonarqube" is the server configured in "Configure System"
        //    withSonarQubeEnv('sonarqube') {
              // Execute the SonarQube scanner with desired flags
        //      sh "${scannerHome}/bin/sonar-scanner \
        //                  -Dsonar.projectKey=pipeline \
        //                  -Dsonar.projectName=pipeline \
        //                  -Dsonar.projectVersion=0.0.${BUILD_NUMBER} \
         //                 -Dsonar.host.url=https://fb676f7229dd1e.lhrtunnel.link/ \
         //                 -Dsonar.sources=. \
         //                 -Dsonar.login=admin \
         //                 -Dsonar.password=admin1 "
         //   }       
         // }
      
      //stage('Build docker-image') {
       // steps {
       //   sh "cd ./${PROJECT_ROOT};docker build -t ${REGISTRY}:${BUILD_NUMBER} . "
       // }
      //}
      //stage('Deploy docker-image') {
      //  steps {
          // If the Dockerhub authentication stopped, do it again
      //    sh 'docker login'
      //    sh "docker push ${REGISTRY}:${BUILD_NUMBER}"
      //  }
      }        
    }
}