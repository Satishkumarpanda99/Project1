@Library('Jenkins-SharedLib@main') _
pipeline {
    agent any
    tools {
        maven 'local_maven'
    }
    parameters {
         string(name: 'staging_server', defaultValue: '3.111.198.203', description: 'Remote Staging Server')
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
