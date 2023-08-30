pipeline {
    agent any

    stages {
        stage('Create Release in QA') {
            steps {
                // ... Steps to create the release in the QA branch
            }
        }
        stage('Trigger Central Jenkinsfile') {
            steps {
                build job: 'Central-Jenkinsfile', parameters: [
                    string(name: 'branch', value: 'QA'),
                    string(name: 'tag', value: 'v.1')
                ]
            }
        }
    }
}
