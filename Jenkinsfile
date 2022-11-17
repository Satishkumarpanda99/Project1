pipeline {
    agent any
    tools {
        maven 'local_maven'
    }
    environment {
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
    }
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage ('build') {
        steps {
            sh 'mvn clean package'
        }
        post {
            success {
                echo 'archiving artifacts'
                archiveArtifacts artifacts: '**/target/*.war'
                sh 'aws configure set region ap-south-1'
                sh 'aws s3 cp ./target/*.war s3://fudzeo'
                emailext attachLog: true, body: 'success build ', subject: 'jenkins-success', to: 'j.jyotiranjan29@gmail.com'
            }
            failure {
                    emailext attachLog: true, body: 'success build ', subject: 'jenkins-failure', to: 'j.jyotiranjan29@gmail.com'
                }
        }
        }
        stage ('deploye') {
            steps {
                sshagent(['deploy-tomcat']) {
                    sh "scp -v -o StrictHostKeyChecking=no **/*.war ec2-user@13.233.76.195:/opt/tomcat/webapps/"
      }
            }
        }
    }
}
