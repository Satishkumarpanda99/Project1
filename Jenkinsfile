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
                  emailext attachLog: true, body: 'congratulation your build is success', recipientProviders: [buildUser()], subject: 'success build', to: 'satishkumarpanda1999@gmail.com'
                       }
                failure {
                    emailext body: 'sorry your build is faild', subject: 'failure build', to: 'satishkumarpanda1999@gmail.com
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
