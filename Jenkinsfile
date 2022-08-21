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
          emailext body: 'Test Message',
    subject: 'Test Subject',
    to: 'jyoti.swain123@gmail.cm'
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
