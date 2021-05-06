pipeline {
    agent {

        node {
            label 'iOSVirt'

        }
    }

    stages {

        stage('to run on BBB') {
            agent {
                label 'iOSVirt'
            }
            steps {

                sh ' echo /'make/''

            }

        }