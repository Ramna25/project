pipeline {
    agent any

    stages {
        stage('Start') {
            steps {
                script {
                    def branchname = env.BRANCH_NAME
                    def tag = sh(script: "git tag --sort version:refname | tail -1", returnStdout: true).trim()
                    def repotag = sh(script: "git tag --contains HEAD | head -1", returnStdout: true).trim()
                    def gitrepo = scm.getUserRemoteConfigs()[0].getUrl()
                    def reponame = gitrepo.tokenize('/').last().split("\\.")[0]

                    echo "Branch Name: ${branchname}"
                    echo "Latest Tag: ${tag}"
                    echo "Latest Commit Tag: ${repotag}"
                    echo "Repository URL: ${gitrepo}"
                    echo "Repository Name: ${reponame}"

                    build job: 'main', wait: false, parameters: [
                        string(name: 'branchname', value: branchname),
                        string(name: 'reponame', value: reponame),
                        string(name: 'gitrepo', value: gitrepo),
                        string(name: 'repotag', value: repotag)
                    ]
                }
            }
        }
    }
}
