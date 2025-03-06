pipeline{
    agent{
        Docker{
            image "cypress/browsers"
            args " --entrypoint=''"
        }
    }


    stages{
        stage("npm installation"){
            steps{
                sh "npm ci"
            }
        }
        stage("tests exec"){
            steps{
                sh "npx cypress run"
            }
        }
    }

    // générer les rapports
    post{
        always {
            archiveArtifacts artifacts: 'cypress/reports/cucumber/**/*.json', allowEmptyArchive: true
            cucumber buildStatus: '', fileIncludePattern: 'cypress/reports/cucumber/**/*.json'
        }
    }

}