#!/usr/bin/env groovy
pipeline {
    options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    agent {
        kubernetes {
            cloud 'kubernetes'
            defaultContainer 'jnlp' 
        }
    }
    parameters {
        string(name: 'BRANCH', defaultValue: 'master', description: 'Choose git branch')
        string(name: 'MAIL', defaultValue: 'pavel.sinelnik@regula.by', description: 'Choose mail address')
    }
    stages {
        stage('Run tests') {
            parallel {
                stage("Run on Mac"){
                    steps {
                        checkout([
                            $class: 'GitSCM',
                            branches: [[name: '${BRANCH}']],
                            userRemoteConfigs: [[url: 'https://github.com/PavelSinelnik/Jenkins_test.git']]
                        ])
                        sh '''name="$(cat name.txt)"
                        echo "hello $name"
                        '''
                    }
                } 
            }
        } 
    }
    post{
        success {
            emailext (
                    subject: "[Jenkins][SUCCESS] '${JOB_NAME} [${BUILD_NUMBER}]'",
                    body: '''
                    Build '${JOB_NAME} [${BUILD_NUMBER}]': was successfull                   
                    ''',
                    to: '${MAIL}',
                    mimeType: 'text/html'
            )
        }
        failure {
            emailext (
                    subject: "[Jenkins][FAILED] '${JOB_NAME} [${BUILD_NUMBER}]'",
                    body: '''
                    Build '${JOB_NAME} [${BUILD_NUMBER}]': failed                  
                    ''',
                    to: '${MAIL}',
                    mimeType: 'text/html'
            )
        }
        aborted {
            emailext (
                    subject: "[Jenkins][ABORTED] '${JOB_NAME} [${BUILD_NUMBER}]'",
                    body: '''
                    Build '${JOB_NAME} [${BUILD_NUMBER}]': was aborted
                    ''',
                    to: '${MAIL}',
                    mimeType: 'text/html'
            )
        }
        
    } 
}