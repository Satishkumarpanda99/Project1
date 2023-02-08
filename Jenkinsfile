pipeline {
    agent any
    tools {
        maven 'local_maven'
    }
stages {
    stage('build') {
        steps{
            sh 'mvn clean package'
        }
        post {
            success {
                echo 'archiving the artifacts'
                archiveArtifacts artifacts: '**/target/*.war'
            }
        }
    }
    stage ('deploy'){
        steps{
            echo 'deploy success'
        }
    }
}
}
