pipeline {

    agent any

    environment {

        JFROG_CLI_BUILD_NAME = "${env.JOB_NAME}"

        JFROG_CLI_BUILD_NUMBER = "${env.BUILD_NUMBER}"

    }

    tools {
        maven 'maven'
        jdk 'jdk'
    }

    stages {
        
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                    echo "${WORKSPACE}"
                '''
            }
        }

        stage ('Download Syft') {
            steps {
                sh 'mkdir -p ~/anchore-tools && cd ~/anchore-tools && curl -sSfL https://raw.githubusercontent.com/anchore/syft/main/install.sh | sh -s -- -b .'
            }
        }

        stage ('Run Maven') {

            steps {

                sh 'pwd && ls -la && cd ${WORKSPACE} && mvn clean install' // build & deploy artifacts


            }

        }
        stage ('Scan built maven project with Syft') {

            steps {

                sh './syft .' // Scan with Syft

            }

        }

    }

}