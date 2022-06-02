pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Deploy') {
            input message: 'Ready to deploy? (Click "Proceed" to continue)'
            steps {
                sh './scripts/deploy.sh'
            }
        }
    }
}