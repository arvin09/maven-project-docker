pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                bat 'mvn clean package'
                bat 'docker build . -t tomcatwebapp:${evn.BUILD_ID}'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}