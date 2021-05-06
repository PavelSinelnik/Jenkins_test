pipeline {
    agent {
            label 'Android'
        }


    stages {

        stage('to run on BBB') {

            steps {
                sleep 7
                powershell script("Get-Childitem")
                powershell script("Get-Location")
            }

        }
    }
}