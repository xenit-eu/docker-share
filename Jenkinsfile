pipeline {
    agent any
    stages {
        stage("Build Docker Image") {
            steps {
                sh "./gradlew -Penterprise buildDockerImage"
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
                sh "./gradlew -Penterprise pushDockerImage"
            }
        }
    }
}
