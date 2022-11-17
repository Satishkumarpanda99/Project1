pipeline {
    agent any
    tools {
        maven 'local_maven'
    }
    environment {
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
    }
    parametars {
        string (name: 'tomcat', defaultvalue: '', description 'deployment')
    }   
    trigger {
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
                archiveArtifacts '**/target*.war'
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
                       sh "scp -v -o StrictHostKeyChecking=no **/*.war ec2-user@35.154.176.61:/opt/tomcat/webapps/"
      }
            }
        }
    }
}
