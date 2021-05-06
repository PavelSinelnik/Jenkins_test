#!/usr/bin/env groovy
pipeline {
    agent {
            label 'Android'
        }


    stages {

        stage('to run on BBB') {

            steps {
                echo "hello"
                node {
    powershell 'Write-Output "Hello, World!"'
}
            }

        }

    }

}