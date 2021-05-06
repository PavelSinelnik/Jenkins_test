pipeline {
    agent {
            label 'Android'
        }


    stages {

        stage('to run on BBB') {

            steps {
                sleep 7
                powerShell ("""Get-Childitem""")
                powerShell ("""Get-Location""")
            }

        }
    }
}