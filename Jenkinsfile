pipeline {
    agent any

    parameters {
        string(name: 'branchname', defaultValue: '', description: 'Branch name')
        string(name: 'latestTag', defaultValue: '', description: 'Tag name')
    }

    stages {
        stage('Check Release') {
            steps {
                script {
                    def branchname = params.branch
                    def tag = params.tag

                    echo "Received branch: ${branchname}"
                    echo "Received tag: ${latestTag}"

                    if (branchname == 'QA' && tag.startsWith('qa-')) {
                        echo "I am a release from QA."
                    } else if (branchname == 'sandbox' && tag.startsWith('sandbox-')) {
                        echo "I am a release from sandbox."
                    } else {
                        echo "This is not a recognized release."
                    }
                }
            }
        }
    }
}

