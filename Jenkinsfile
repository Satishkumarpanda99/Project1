pipeline {
    agent any
    
    tools {
        maven 'local_maven'
    }
stages{
    stage('junit_Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit '**/target/*.xml'
                }
            }
        }
    stage('Build'){
            steps {
                sh 'mvn -s settings.xml -DeskipTests install'
            }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    stage('Test') {
        steps {
           sh 'mvn -s settings.xml test'
        }
    }
    stage('Checkstyle Analysis') {
        steps {
           sh 'mvn -s settings.xml checkstyle:checkstyle'
        }
    }
   
        stage ('Deployments'){
                             steps {
                       echo 'Deploy success'
                    }
                }
    }
}
