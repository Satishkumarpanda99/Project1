pipeline {
    agent any
    tools {
        maven 'local_maven'
    }
stages{
        stage('Build'){
            steps {
                bat 'mvn clean package'
            }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                    emailext body: 'Test Message',
    recipientProviders: [developers(), requestor()],
    subject: 'Test Subject'
                }
            }
        }

        stage ('Deployments'){
            steps {
            echo 'successful Deploy'
            }
        }
    }
}
