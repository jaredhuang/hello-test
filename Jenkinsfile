pipeline {
    agent any

    stages {
        stage('Complie Stage') {
            steps {
                withMaven(maven : 'maven_3_3_9') {
                    sh 'mvn clean compile'

                }
            }
        }

        stage('Testing Stage') {
            steps {
                withMaven(maven : 'maven_3_3_9') {
                    sh 'mvn test'
                }
            }
        }
        
        stage('SonarQube analysis') {
            def sonarqubeScannerHome = tool name: 'Sonar Scanner'
            withSonarQubeEnv('SonarQube') {
              sh "${sonarqubeScannerHome}/bin/sonar-scanner"
            }
        }

        stage('Deploy Stage') {
            steps {
                withMaven(maven : 'maven_3_3_9') {
                    sh 'mvn install'
                }
            }
        }
    }
}

