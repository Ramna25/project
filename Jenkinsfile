pipeline {
    agent any

    stages {
        stage('Create Release in QA') {
            steps {
                echo "Creating release in QA branch..."
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
