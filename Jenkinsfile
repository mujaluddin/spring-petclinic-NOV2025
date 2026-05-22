pipeline {
    agent any

    tools {
        jdk 'jdk21'
        maven 'maven'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/mujaluddin/spring-petclinic-NOV2025.git'
            }
        }

        stage('Build Application') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }
    }

    post {
        success {
            echo 'Build successful'
        }

        failure {
            echo 'Build failed'
        }
    }
}