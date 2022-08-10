pipeline {
    agent any
    tools {
        maven 'local_maven'
    }

    parameters {
         string(name: 'tomcat_stag', defaultValue: '35.154.81.229', description: 'Tomcat Staging Server')
    }

stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }

        stage ('Deployments'){
                stage ('Deploy to Staging Server'){
                    steps {
                        sshagent(['b0962c0e-e3d6-4ff1-8cca-7a282bad7546']) {
                        sh "scp **/*.war jenkins@${params.tomcat_stag}:/usr/share/tomcat/webapps"
      }
                    }
                }
            }
        }
    }
}
