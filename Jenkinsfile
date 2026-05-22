pipeline {
    agent any

    tools {
        maven 'Maven3'
        jdk 'JDK17'
    }

    stages {

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Run') {
            steps {
                sh 'mvn exec:java -Dexec.mainClass=com.example.app.App'
            }
        }
    }

    post {
        always {
            emailext(
                subject: "Jenkins Build: ${currentBuild.currentResult}",
                body: "Job: ${JOB_NAME}\nBuild: ${BUILD_NUMBER}\nStatus: ${currentBuild.currentResult}\nURL: ${BUILD_URL}",
                to: "abhishekms1234.x@gmail.com"
            )
        }
    }
}
