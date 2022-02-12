pipeline {

    agent any

    environment {

        JFROG_CLI_BUILD_NAME = "${env.JOB_NAME}"

        JFROG_CLI_BUILD_NUMBER = "${env.BUILD_NUMBER}"

    }

    tools {
        maven 'Maven 3.8.4'
        jdk 'jdk9'
    }

    stages {
        
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }

        stage ('Run Maven') {

            steps {

                sh 'mvn clean install' // build & deploy artifacts


            }

        }

    }

}