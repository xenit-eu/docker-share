pipeline {
    agent any
    stages {
        stage("Build Docker Image") {
            steps {
                sh "./gradlew buildDockerImage"
            }
        }

        stage("Unit Tests") {
            steps {
                sh "./gradlew test"
            }
        }

        stage("Integration Tests") {
            steps {
                sh "./gradlew integrationTests --info"
            }
            post {
                always {
                    sh "./gradlew composeDown"
                }
            }
        }

        stage("Publish Docker Image") {
            when {
                anyOf {
                    branch 'master'
                    branch 'release*'
                }
            }
            steps {
                sh "./gradlew pushDockerImage"
            }
        }
    }
}
