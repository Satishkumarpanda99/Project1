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
                    emailext body: 'congratulation your build is success', subject: 'success build', to: 'jyoti.swain123@gmail.com'
                       }
                failure {
                    emailext body: 'sorry your build is faild', subject: 'failure build', to: 'jyoti.swain123@gmail.com'
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
