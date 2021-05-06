pipeline {
    agent {

        node {
            label 'Android'

        }
    }

    stages {

        stage('to run on BBB') {
            agent {
                label 'Android'
            }
            steps {

                sh ' echo /'make/''

            }

        }