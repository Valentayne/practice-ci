pipeline {
    agent {
        docker {
            image 'maven:3.9.9-eclipse-temurin-11'
            args '-v /root/.m2:/root/.m2'
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
            post {
                always {
                    junit 'Java/target/surefire-reports/*.xml' 
                }
            }
        }
    }
}
