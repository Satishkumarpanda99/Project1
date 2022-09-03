@Library('Jenkins-SharedLib@dev1') _
pipeline {
    agent any
    tools {
        maven 'local_maven'
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
