pipeline {
    agent { label 'maven' }
    environment {
        PATH = "/opt/apache-maven-3.9.9/bin:$PATH"
    }
    stages {
        stage('SCM Checkout') {
            steps {
                git branch: 'main', credentialsId: 'github-cred', url: 'https://github.com/asifkhazi/devops-workshop-2.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install -Dmaven.test.skip=true'
            }
        }

        stage('test') {
            steps {
                sh 'mvn surefire-report:report'
            }
        }
    }
}
