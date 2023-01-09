pipeline {
    agent any
    
    tools {
        maven 'local_maven'
    }
stages{
       stage('SonarQube analysis') {
    withSonarQubeEnv('sonarqube-9.8') { 
      // You can override the credential to be used
      sh 'mvn sonar:sonar'
    }
  }
    stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage ('Deployments'){
                             steps {
                       echo 'Deploy success'
                    }
                }
    }
}
