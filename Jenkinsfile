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
                       sh "scp -o StrictHostKeyChecking=no **/*.war ec2-user@35.154.176.61:/opt/tomcat/webapps/"
      }
                    }
                }
    }
}
