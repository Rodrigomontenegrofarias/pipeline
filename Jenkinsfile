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
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
        stage('scan') {
          environment {
             //Previously defined in the Jenkins "Global Tool Configuration"
            scannerHome = 'sonar-scanner'
          }
            steps {
             //"sonarqube" is the server configured in "Configure System"
              withSonarQubeEnv('sonarqube') {
              // Execute the SonarQube scanner with desired flags
              sh "${scannerHome}/bin/sonar-scanner \
                          -Dsonar.projectKey=rodrigo \
                          -Dsonar.sources=. \
                          -Dsonar.host.url=http://localhost:9000 \
                          -Dsonar.login=admin\
                          -Dsonar.password=admin1"
           }
          }
            
        }
        
        stage('Build docker-image') {
            steps {
            sh "cd ./${PROJECT_ROOT};docker build -t ${REGISTRY}:${BUILD_NUMBER} . "
            }
        }
        stage('Deploy docker-image') {
            steps {
            // If the Dockerhub authentication stopped, do it again
            sh 'docker login'
            sh "docker push ${REGISTRY}:${BUILD_NUMBER}"
            }
       }
    }
}