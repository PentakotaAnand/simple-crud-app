pipeline {
    agent any 
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM',
                          branches: [[name: '*/master']],
                          extensions: [[$class: 'CleanBeforeCheckout']],
                          credentialsId: 'f5a3f566-98df-44c6-9e75-69339212f2c9',
                          url: 'https://github.com/PentakotaAnand/simple-crud-app.git'])
            }
        }
        stage('Code analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    withMaven(maven:'Maven 3.5') {
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
    }
}
