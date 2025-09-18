pipeline {
    agent any

    tools {
        maven 'mvn' // Updated tool name
    }

    stages {
        stage('Build') {
            steps {
                withMaven(maven: 'mvn') {
                    sh 'mvn clean install'
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
