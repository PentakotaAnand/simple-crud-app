pipeline {
    agent any 
    stages {
        stage('Code analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    withMaven(maven:'Maven') {
                        sh 'mvn clean package sonar:sonar'
                    }
                }
                timeout(time: 2, unit: 'MINUTES'){
                    waitForQualityGate abortPipeline:true
                }
            }
        }

    }
}

