pipeline {
    agent any

    stages {
        stage('Create Release in QA') {
            steps {
                script {
                    def branchname = env.BRANCH_NAME
                    def Tag = sh(script: "git describe --tags --abbrev=0", returnStdout: true).trim()

                    echo "Creating release in ${branchname} branch..."
                    
                    
                }
            }
        }
        stage('Trigger Central Jenkinsfile') {
            steps {
                script {
                    def branchname = env.BRANCH_NAME
                    def Tag = sh(script: "git describe --tags --abbrev=0", returnStdout: true).trim()

                    build job: 'main', parameters: [
                        string(name: 'branch', value: branchname),
                        string(name: 'tag', value: Tag)
                    ]
                }
            }
        }
    }
}
