pipeline {
    agent any
    
    tools {
        maven 'Maven3' 
        jdk 'JDK17'   
    }
    
    triggers {
        pollSCM('H/15 * * * *')
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', fingerprint: true
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
        always {
            echo 'Pipeline finished'
        }
    }
}
