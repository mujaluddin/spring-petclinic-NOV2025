pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    environment {
        APP_NAME = "spring-petclinic"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/mujaluddin/spring-petclinic-NOV2025.git'
            }
        }

        stage('Verify Java & Maven') {
            steps {
                sh '''
                java -version
                mvn -version
                '''
            }
        }

        stage('Clean Project') {
            steps {
                sh 'mvn clean'
            }
        }

        stage('Build Application') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed'
        }

        success {
            echo 'Spring PetClinic build successful'
        }

        failure {
            echo 'Build failed. Please check console logs.'
        }
    }
}