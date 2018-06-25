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
            steps {
            echo "正在开始代码检测........."
            withSonarQubeEnv('Sonar') {
               sh '/usr/local/sonar-scanner/bin/sonar-scanner'
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

