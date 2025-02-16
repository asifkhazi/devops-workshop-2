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

        stage('SonarQube analysis') {
            environment {
                scannerHome = tool 'sonar-scanner'
            }
            steps {
                withSonarQubeEnv('sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}
