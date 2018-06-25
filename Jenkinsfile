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

        stage('SonarQube') {
            withSonarQubeEnv('Sonar') {
                sh "mvn -f pom.xml clean compile sonar:sonar"
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

