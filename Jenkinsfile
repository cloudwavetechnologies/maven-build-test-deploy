pipeline {
    agent any

    tools {
        maven 'maven_3_5_0'
    }

    stages {
        stage('Compile Stage') {
            steps {
                withMaven(maven: 'maven_3_5_0') {
                    sh 'mvn clean install'
                }
            }
        }

        // Optional Testing Stage
        /*
        stage('Testing Stage') {
            steps {
                withMaven(maven: 'maven_3_5_0') {
                    sh 'mvn test'
                }
            }
        }
        */

        stage('Deployment Stage') {
            steps {
                sh '/usr/local/bin/aws s3 cp target/supplychain-project-1.0-SNAPSHOT.jar s3://supplychain-s3-000/'
                sh '/usr/local/bin/aws s3 ls'
                sh '/usr/local/bin/aws s3 ls s3://supplychain-s3-000/'
            }
        }
    }
}
