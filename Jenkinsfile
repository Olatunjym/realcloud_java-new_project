pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                sh 'cd SampleWebApp mvn test'
            }
        }
        stage('Build') {
            steps {
                sh 'cd SampleWebApp && mvn clean package'
            }
        }
        
        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [tomcat8(credentialsId: 'tomcat', path: '', url: 'http://35.168.18.93:8080/')], contextPath: 'webapp', war: '**/*.war'
            }
        }
    }
}
