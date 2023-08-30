pipeline {
    agent any

    stages {
        stage('Create Release in sandbox') {
            steps {
                echo "Creating release in sandbox branch..."
            }
        }
        stage('Trigger Central Jenkinsfile') {
            steps {
                build job: 'Central-Jenkinsfile', parameters: [
                    string(name: 'branch', value: 'sandbox'),
                    string(name: 'tag', value: 'v.1')
                ]
            }
        }
    }
}
