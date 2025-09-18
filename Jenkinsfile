pipeline {
    agent any

    tools {
        maven 'mvn' // This matches your updated tool name
    }

    stages {
        stage('Build') {
            steps {
                script {
                    def mvnHome = tool 'mvn'
                    sh "${mvnHome}/bin/mvn clean install"
                }
            }
        }

        stage('Deploy to S3') {
            steps {
                sh '/usr/local/bin/aws s3 cp target/supplychain-project-1.0-SNAPSHOT.jar s3://supplychain-s3-000/'
                sh '/usr/local/bin/aws s3 ls s3://supplychain-s3-000/'
            }
        }
    }
}
