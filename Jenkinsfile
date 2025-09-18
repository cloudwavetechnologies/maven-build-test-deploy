pipeline {
    agent any

    tools {
        maven 'maven_3_5_0' // Ensure this matches your Jenkins tool config
    }

    stages {
        stage('Build') {
            steps {
                withMaven(maven: 'maven_3_5_0') {
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
