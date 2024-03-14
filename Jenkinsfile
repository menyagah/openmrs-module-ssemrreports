pipeline {
    agent {
        label "jenkins-agent"
    }

    tools {
        jdk 'Java17'
        maven 'Maven3'
    }
    
    stages {
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
            }
        }
        
        stage('Checkout from scm') {
            steps {
                git branch: 'main', credentialsId: 'github-jenkins', url: 'https://github.com/menyagah/openmrs-module-ssemrreports'
            }
        }
        
        stage('Build Application') {
            steps {
                sh "mvn clean package"
            }
        }
        stage('Test Application') {
            steps {
                sh "mvn test"
            }
        }
    }
}