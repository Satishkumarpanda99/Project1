pipeline {
    agent any
    tools {
        maven 'local_maven'
    }
    environment {
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
    }      
stages {
    stage('build') {
        steps{
            sh 'mvn clean package'
        }
        post {
            success {
                    archiveArtifacts 'target/*.war'
                    sh 'aws configure set region ap-south-1'
                    sh 'aws s3 cp ./target/*.war s3://fudzeo'
            }
        }
    }
    stage ('deploy'){
        steps{
          echo 'deploy success'
        }
    }
}
}
