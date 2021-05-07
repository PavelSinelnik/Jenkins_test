#!/usr/bin/env groovy
pipeline {
options {
    buildDiscarder(logRotator(numToKeepStr: '30'))
  }
    agent none
        parameters {
        string(name: 'BRANCH', defaultValue: 'master', description: 'Choose git branch')
        }
    stages {

        stage('Run tests') {
          parallel{
            stage("Run on windows"){
              agent{ label "Android"}
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '${BRANCH}']],
                    userRemoteConfigs: [[url: 'https://github.com/PavelSinelnik/Jenkins_test.git']]
                ])
                bat '''
                  ECHO hello world
                  PAUSE
                '''
            }


            } //stage after parallel
            stage("Run on Mac"){
                agent { label "iOSVirt"}
                steps{

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



//        stage('ls repo') {
//            steps {
//                sh '''name="$(cat name.txt)"
//                echo "hello $name"
//                '''
//                   bat '''
 //                  ECHO HELLO WORLD
 //                  PAUSE
  //                 '''

}