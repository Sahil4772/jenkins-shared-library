pipeline {
    agent any

    tools {
        maven 'Maven 3.5.2'
    }
    environment {
        MAVEN_OPTS = ' -Denv.build-timestamp=${BUILD_TIMESTAMP} ...'
    }
    stages {

        stage ('Build') {
            steps {
                bat 'mvn -Dmaven.test.failure.ignore=true clean install'.
            }
            post {
                success {
                    junit 'target/surefire-reports/*.xml'.

                    jacoco classPattern: '**/target/classes',
                           execPattern: '**/target/coverage-reports/jacoco-ut.exec',
                           sourcePattern: '**/src/org/yourcompany',
                           exclusionPattern: '**/target/classes/*closure*.class'
                }
            }
        }
    }
}
