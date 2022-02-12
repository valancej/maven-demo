pipeline {

    agent any

    environment {

        JFROG_CLI_BUILD_NAME = "${env.JOB_NAME}"

        JFROG_CLI_BUILD_NUMBER = "${env.BUILD_NUMBER}"

    }

    stages {

        stage ('Run Maven') {

            steps {

                sh 'mvn clean install' // build & deploy artifacts


            }

        }

    }

}