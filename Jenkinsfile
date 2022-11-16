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
                    emailext attachLog: true, body: 'success build ', subject: 'jenkins-success', to: 'jyoti.swain123@gmail.com'
                       }
                failure {
                    emailext attachLog: true, body: 'success build ', subject: 'jenkins-failure', to: 'jyoti.swain123@gmail.com'
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
