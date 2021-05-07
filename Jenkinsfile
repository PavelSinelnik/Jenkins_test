#!/usr/bin/env groovy
pipeline {
    agent {
            label 'iOSVirt'
        }
        parameters {
        string(name: 'BRANCH', defaultValue: 'master', description: 'Choose git branch')
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
                sh "echo 'hello'"
                sh "ls"
            }
        }
    }
}