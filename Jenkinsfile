pipeline {
    agent any

    stages {
        stage('Start') {
            steps {
                script {
                    def branch = env.BRANCH_NAME
                    def tag = sh(script: "git tag --sort version:refname | tail -1", returnStdout: true).trim()
                    def repotag = sh(script: "git tag --contains HEAD | head -1", returnStdout: true).trim()
                    def latestTag = sh(script: "git describe --tags --abbrev=0", returnStdout: true).trim()
                    def gitrepo = scm.getUserRemoteConfigs()[0].getUrl()
                    def reponame = gitrepo.tokenize('/').last().split("\\.")[0]

                    echo "Branch Name: ${branch}"
                    echo "Latest Tag: ${tag}"
                    echo "Latest Tag: ${latesTag}"
                    echo "Latest Commit Tag: ${repotag}"
                    echo "Repository URL: ${gitrepo}"
                    echo "Repository Name: ${reponame}"

                    build job: 'main', wait: false, parameters: [
                        string(name: 'branch', value: branch),
                        string(name: 'reponame', value: reponame),
                        string(name: 'gitrepo', value: gitrepo),
                        string(name: 'tag', value: tag),
                        string(name: 'repotag', value: repotag),
                        string(name: 'latestTag', value: latestTag)
                    ]
                }
            }
        }
    }
}
