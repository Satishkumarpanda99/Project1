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
            deploy adapters: [tomcat7(credentialsId: '78022f04-c7fa-45bb-851e-f6bb3b7e3ff0', path: '', url: 'http://3.111.198.203:8282/')], contextPath: null, war: '**/*.war'
        }
    }
 }
}
