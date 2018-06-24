pipeline {
    agent any

    stages {
        stage('Complie Stage') {
            steps {
                withMaven(maven : 'mvn') {
                    sh 'mvn clean compile'

                }
            }
        }

        stage('Testing Stage') {
            steps {
                withMaven(maven : 'mvn') {
                    sh 'mvn test'
                }
            }
        }

        stage('Deploy Stage') {
            steps {
                withMaven(maven : 'mvn') {
                    sh 'mvn deploy'
                }
            }
        }
    }
}
