pipeline {
    agent any
    
    tools {
        maven 'local_maven'
    }
stages{
stage('junit_Test') {
            steps {
                sh 'pip install pytest-junit'
                sh 'python -m pytest --junitxml=junit.xml'
            }
            post {
                always {
                    junit 'junit.xml'
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
