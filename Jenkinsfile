pipeline {
    agent any

    parameters {
        string(name: 'branch', defaultValue: '', description: 'Branch name')
        string(name: 'tag', defaultValue: '', description: 'Tag name')
    }

    stages {
        stage('Check Release') {
            steps {
                script {
                    def branch = params.branch
                    def tag = params.tag

                    echo "Received branch: ${branch}"
                    echo "Received tag: ${tag}"

                    if (branch == 'QA' && tag.startsWith('qa-')) {
                        echo "I am a release from QA."
                    } else if (branch == 'sandbox' && tag.startsWith('sandbox-')) {
                        echo "I am a release from sandbox."
                    } else {
                        echo "This is not a recognized release."
                    }
                }
            }
        }
    }
}

