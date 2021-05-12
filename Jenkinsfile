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
    }
    stages {
        stage('Run tests') {
            parallel {
                stage("Run on Mac"){
                    agent { label "jnlp" }
                    steps {
                        checkout([
                            $class: 'GitSCM',
                            branches: [[name: '${BRANCH}']],
                            userRemoteConfigs: [[url: 'https://github.com/PavelSinelnik/Jenkins_test.git']]
                        ])
                        sh '''name="$(cat name.txt)"
                        echo "hello $name"
                        '''
                    }//after steps MAC
                } //after stage MAC
            }//stage nad parallel
        } //parallel
    } //main stages
}