pipeline {
    agent any
    
    tools {
        maven 'local_maven'
    }
stages{
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
                        sshagent(['deploy-tomcat']) {
                       sh "scp -v -o StrictHostKeyChecking=no **/*.war ec2-user@13.201.61.5:/opt/tomcat/webapps/"
      }
                    }
                }
    }
}
