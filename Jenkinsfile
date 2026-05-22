cd ~/demo-app
nano Jenkinsfilepipeline {

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
                sh 'mvn exec:java -Dexec.mainClass="com.example.app.App"'
            }
        }

    }

    post {

        always {
            emailext(
                subject: "Jenkins Build: ${currentBuild.currentResult}",
                body: """
Job Name: ${JOB_NAME}

Build Number: ${BUILD_NUMBER}

Status: ${currentBuild.currentResult}

Build URL: ${BUILD_URL}
                """,
                to: "abhishekms1234.x@gmail.com"
            )
        }

    }

}
