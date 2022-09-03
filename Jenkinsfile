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
                    emailext body: 'email test', subject: 'test', to: 'j.jyotiranjan29@gmail.com'
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
