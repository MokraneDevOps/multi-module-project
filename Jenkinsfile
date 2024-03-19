pipeline {
    agent {
        label 'jenkins-slave-docker-node'
    }
    stages {
        stage('Compile') {
            steps {
                script {
                    sh "mvn clean compile"
                }
            }
        }
        stage('Unit Test') {
            steps {
                script {
                    sh "mvn test"
                }
            }
        }
        stage('Package') {
            steps {
                script {
                    sh "mvn package assembly:single"
                }
            }
        }
        stage('Install') {
            steps {
                script {
                    sh "mvn install"
                }
            }
        }
        stage('Execute') {
            steps {
                script {
                    def jarPath = '/tmp/workspace/docker-slave-sanchez/main/target/main-1.0.0-SNAPSHOT-jar-with-dependencies.jar'
                    sh "java -jar ${jarPath}"
                }
            }
        }
    }
}
