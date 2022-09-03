@Library('Jenkins-SharedLib') _
pipeline {
    agent any
    tools {
        maven 'localMaven'
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
                stage ('Deploy to Staging Server'){
                    script {
                        deploy ()
                    }
                }
            }
        }
    }
}
