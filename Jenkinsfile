pipeline {
    agent any

    tools {
        jdk 'JAVA-21'
        maven 'MAVEN-3.9.16'
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
            echo 'Build completed successfully'
        }

        failure {
            echo 'Build failed'
        }
    }
}