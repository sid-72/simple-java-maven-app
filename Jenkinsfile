pipeline {
    agent { 
        node {
            label 'docker-agent-alpine'
            }
      }
    triggers {
        pollSCM '*/5 * * * *'
    }
    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                apk add maven
                mvn package
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                java -jar target/my-app-1.0-SNAPSHOT.jar
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                echo "doing delivery stuff.."
                '''
            }
        }
    }
}