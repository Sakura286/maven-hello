pipeline {
    agent {
        docker {
            image 'maven:3.9.6'
            args '-u root'
        }
    }
    environment {
        MY_NAME = 'Sakrua286'
        MY_MACHINE    = 'my-spoon'
    }
    stages {
        stage('Print Version') {
            steps {
                sh 'mvn --version'
            }
        }
        stage('Build') {
            steps {
                sh 'pwd'
                sh 'mvn package'
            }
        }
        stage('Sanity Check') {
            steps {
                input 'Does the output look ok?'
            }
        }
    }
    post {
        always {
            echo 'This will always run'
            archiveArtifacts artifacts: 'target/maven-hello-1.0-SNAPSHOT.jar', fingerprint: true
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
