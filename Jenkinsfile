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
                        sshagent(['b0962c0e-e3d6-4ff1-8cca-7a282bad7546']) {
                            script {
                                 deploy_tomcat ()
                            }
      }
                    }
        }
    }
}
