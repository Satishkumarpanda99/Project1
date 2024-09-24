pipeline {
    agent any 
    tools {
        maven 'Maven'
    }

     environment {
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
    }      

    stages {
        stage('Build') {
            steps{
            echo 'build'
            }
        }
        stage('Test') {
            steps {
           echo 'test'
            }
        }
        stage('Publish') {
            steps {
                sh 'mvn package'
            }
             stage('aws cli install') {
            steps {
                sh 'sudo yum install awscli'
            }
            post {
                success {
                    archiveArtifacts 'target/*.war'
                    sh 'aws configure set region ap-south-1'
                    sh 'aws s3 cp ./target/*.war s3://jenkinsucket01'
                }
            }
        }
    }
}
