pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Run Maven on a Unix agent.
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        stage('Deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: '920c26a7-8406-4ee1-88d8-0ddabab27b2a', path: '', url: 'http://ec2-13-59-67-61.us-east-2.compute.amazonaws.com:8080/')], contextPath: 'javawebapp', war: '**/hello-world-0.0.1.war'
            }
        }
    }
}
