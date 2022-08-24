pipeline {
    agent any
    tools {
        maven 'local_maven'
    }
stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
                }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                    emailext (body: 'hello', subject: 'test', to: 'jyoti.swain123@gmail.com')
                      }
                
            }
        }
        stage ('Deployments'){
                try {
      // you need cloudbees aws credentials
     withCredentials([<object of type com.cloudbees.jenkins.plugins.awscredentials.AmazonWebServicesCredentialsBinding>]) {
    sh "aws s3 cp **/*.war s3://fudzeo"
         }
      } catch(err) {
         sh "echo error in sending artifacts to s3"
      }
        }
    }
}
