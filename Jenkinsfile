@Library('Jenkins-SharedLib@main') _
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
                        deploy adapters: [tomcat7(credentialsId: '8d79c1e7-8b52-4552-9750-fb9f306df2a6', path: '', url: 'http://13.233.5.122:8282/')], contextPath: null, war: '**/*.war'
                            
                    }
        }
    }
}
