pipeline {
    agent any

    stages {
        stage('Build') {
            steps {

                // To run Maven on a Windows agent, use
                 bat "mvnw -Dmaven.test.failure.ignore=true clean package"
            }

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    junit '**/target/surefire-reports/*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}
