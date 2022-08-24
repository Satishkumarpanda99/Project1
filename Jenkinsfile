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
            steps {
                try {
      // you need cloudbees aws credentials
     withCredentials([$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AKIA2E3PY3UTLORJ5MHC', credentialsId: 'deploytos3', secretKeyVariable: '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']) {
    sh "aws s3 cp **/*.war s3://fudzeo"
         }
      } catch(err) {
         sh "echo error in sending artifacts to s3"
      }
        }
}
    }
}
