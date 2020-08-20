pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "maven-3"
    }

    stages {
        stage('Code') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/abprakash405/maven-war.git'
            }
           
        }
stage('Build') {
            steps {

                // Run Maven on a Unix agent.
                bat "mvn -Dmaven.test.failure.ignore=true clean package"

            }
           
        }
stage('Deploy') {
            steps {
                //delete old package if required
                //bat 'curl "http://admin:admin@localhost:8082/manager/text/undeploy?path=/asn-war-example-1.0.0-SNAPSHOT"'
                
                //delete new package
                bat 'curl --upload-file target/asn-war-example-1.0.0-SNAPSHOT.war "http://admin:admin@localhost:8082/manager/text/deploy?path=/asn-war-example-1.0.0-SNAPSHOT"'

            }
           
        }
    }
}
