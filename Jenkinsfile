pipeline {
    agent any

    environment {
        JAVA_HOME = "/usr/lib/jvm/java-21-openjdk-amd64"
        MAVEN_HOME = "/opt/maven/apache-maven-3.9.16"
        PATH = "${JAVA_HOME}/bin:${MAVEN_HOME}/bin:${env.PATH}"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/mujaluddin/spring-petclinic-NOV2025.git'
            }
        }

        stage('Verify Tools') {
            steps {
                sh '''
                    echo "Java Version:"
                    java -version

                    echo "Maven Version:"
                    mvn -version
                '''
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
            echo 'Spring PetClinic build completed successfully'
        }

        failure {
            echo 'Build failed'
        }
    }
}