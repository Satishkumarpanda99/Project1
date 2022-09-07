@Library('Jenkins-SharedLib@main') _
pipeline {
    agent any
    tools {
        maven 'local_maven'
    }
stages {
    stage('Build'){
            steps {
                script {
                    build ()    
                }
            }
        }
    stage ('Deployment') {
        steps {
            script {
            deploy_tomcat ()
            }
        }
    }
 }
}
