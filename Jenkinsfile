#!/usr/bin/env groovy
pipeline {
options {
    buildDiscarder(logRotator(numToKeepStr: '30'))
  }
    agent {
            label 'iOSVirt'
        }
        parameters {
        string(name: 'BRANCH', defaultValue: 'master', description: 'Choose git branch')
        }
    stages {

        stage('Code Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '${BRANCH}']],
                    userRemoteConfigs: [[url: 'https://github.com/PavelSinelnik/Jenkins_test.git']]
                ])
            }
        }


        stage('ls repo') {
            steps {
                sh '''name="$(cat name.txt)"
                echo "hello $name"
                '''
            }
        }
    }
}