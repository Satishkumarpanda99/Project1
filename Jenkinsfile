pipeline {
    tools {
        maven local_maven
    }
stages {
    stage ('Build') {
        parallel {
            stage ('Build server-1') {
                agent {
                    label 'linux'
                }
                steps {
           sh 'mvn clean package'
        }
        post{
            success {
                echo 'Archiving the artifacts'
                archiveArtifacts artifacts: '**/*.war'
            }
        }
            }
            stage ('ProductionBuild sever-2') {
                agent {
                    label 'linux2'
                }
                steps {
           sh 'mvn clean package'
        }
        post{
            success {
                echo 'Archiving the artifacts'
                archiveArtifacts artifacts: '**/*.war'
            }
        }
            }
        }
    }
    stage ('deployment') {
        steps {
            echo 'successful'
        }
    }
 }
}
