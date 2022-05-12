pipeline {
    agent { docker { image 'python:3' } }
    
    environment {
      // General Variables for Pipeline
      PROJECT_ROOT = 'pipeline'
      //EMAIL_ADDRESS = '@gmail.com'
      REGISTRY = 'monteblack1/docker-pruebaz'
    }
    stages {

        stage('Hello') {
            steps {
            // First stage is a sample hello-world step to verify correct Jenkins Pipeline
                echo 'Hello World, I am Happy'
                echo 'This is my amazing Pipeline'
            }
        }    
        stage('build') {
            steps {
                sh 'python --version'
            }
        }
        stage('Checkout') {
            steps {
            // Get Github repo using Github credentials (previously added to Jenkins credentials)
            checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Rodrigomontenegrofarias/pipeline']]])        }
        }
        stage('scan') {
          environment {
            // Previously defined in the Jenkins "Global Tool Configuration"
            scannerHome = tool 'sonar-scanner'
          }
            steps {
            // "sonarqube" is the server configured in "Configure System"
                withSonarQubeEnv('sonarqube') {
              // Execute the SonarQube scanner with desired flags
                sh "${scannerHome}/bin/sonar-scanner \
                          -Dsonar.projectKey=sonarqube \
                          -Dsonar.projectName=sonarqube \
                          -Dsonar.projectVersion=0.0.${BUILD_NUMBER} \
                          -Dsonar.host.url=http://localhost:9000 \
                          -Dsonar.sources=. \
                          -Dsonar.login=83a64ed5d165e1ce740070474097e6426ac72ebd "
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
