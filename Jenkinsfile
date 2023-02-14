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
                emailext attachLog: true, body: 'congratulation your build is successful', subject: 'successful build', to: 'personldata@gmail.com'
                       }
                failure {
                emailext attachLog: true, body: 'sorry your build is successful', subject: 'faild build', to: 'personldata@gmail.com'   
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
