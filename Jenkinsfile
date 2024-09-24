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
            steps {
                echo 'Building the application...'
                sh 'mvn clean install' // Your build command
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'mvn test' // Your test command
            }
        }
        
        stage('Publish') {
            steps {
                echo 'Packaging the application...'
                sh 'mvn package'
            }
        }

       
        
        stage('Upload to S3') {
            steps {
                echo 'Configuring AWS and uploading artifact...'
                sh 'aws configure set region ap-south-1'
                sh 'aws s3 cp ./target/*.war s3://jenkinsucket01'
            }
            post {
                success {
                    echo 'Archiving artifacts...'
                    archiveArtifacts artifacts: 'target/*.war', fingerprint: true
                }
            }
        }
    }
}
