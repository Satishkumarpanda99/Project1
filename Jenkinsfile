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
                    emailext attachLog: true, body: 'success build', subject: 'jenkins-success', to: 'j.yotiranjan29@gmail.com'
                       }
                failure {
                    emailext attachLog: true, body: 'failure build', subject: 'jenkins-failure', to: 'j.yotiranjan29@gmail.com'
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
