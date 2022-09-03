@Library('Jenkins-SharedLib@main') _
pipeline {
    agent any
    tools {
        maven 'local_Maven'
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
