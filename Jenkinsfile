pipeline {
    agent {
        docker {
            image 'maven:3.9.9-eclipse-temurin-8'
        }
    }

    stages {
        stage('Build') {
            steps {
                dir('Java') { 
                    sh 'mvn -B -DskipTests clean package'
                }
            }
        }

        stage('Test') {
            steps {
                dir('Java') {
                    sh 'mvn test'
                }
            }
        }
        post {
            always {
                junit 'Java/target/surefire-reports/*.xml'
                archiveArtifacts artifacts: 'Java/artifact/*.jar', fingerprint: true
            }
        }
    }
}
