pipeline {
    agent { label 'maven' }

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
    }
}
