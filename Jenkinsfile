@Library('Jenkins-SharedLib@main') _
pipeline {
    agent any
    tools {
        maven 'local_maven'
    }
     environment {
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
    }      
stages{
        stage('Build'){
            steps {
                script {
                    build ()    
                }
            }
        }

        stage ('Deployments'){
                steps {
                    script {
                        deploy ()
                    }
                }
            }
        }
    }
