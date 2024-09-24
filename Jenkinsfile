pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                    emailext attachLog: true, body: 'Congratulations, your build is successful', subject: 'Successful Build', to: 'satishkumarpanda1999@gmail.com'
                }
                failure {
                    emailext attachLog: true, body: 'Sorry, your build has failed', subject: 'Failed Build', to: 'satishkumarpanda1999@gmail.com'
                }
            }
        }
        stage('Deployments') {
            steps {
                echo 'Successful Deployment'
            }
        }
    }
}
