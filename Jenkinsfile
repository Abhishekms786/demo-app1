pipeline {

agent any

tools {
maven 'Maven3'
jdk 'JDK17'
}

stages {

stage('Build'){
steps{
sh 'mvn clean compile'
}
}

stage('Test'){
steps{
sh 'mvn test'
}
}

stage('Package'){
steps{
sh 'mvn package'
}
}

stage('Run'){
steps{
sh 'mvn exec:java -Dexec.mainClass="com.example.app.App"'
}
}

}

post {

success {
emailext(
subject:"SUCCESS ${JOB_NAME}",
body:"Build Success ${BUILD_URL}",
to:"abhishekms1234.x@gmail.com"
)
}

failure {
emailext(
subject:"FAILED ${JOB_NAME}",
body:"Build Failed ${BUILD_URL}",
to:"abhishekms1234.x@gmail.com"
)
}

}

}
