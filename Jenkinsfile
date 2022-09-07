@Library('Jenkins-SharedLib@main') _
pipeline {
    agent any
    
    tools {
        maven 'local_maven'
    }
     parameters {
         string(name: 'staging_server', defaultValue: '13.233.5.122', description: 'Remote Staging Server')
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
                        deploy adapters: [tomcat7(credentialsId: 'c7e47893-145b-4a87-8186-7b0c5fa25310', path: '', url: 'http://13.233.5.122:8282/')], contextPath: null, war: '**/*.war'
                            
                    }
        }
    }
}
