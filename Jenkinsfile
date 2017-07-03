node("docker") {
    docker.withRegistry('kirankv369', 'docker-hub-credentials') {
    
        git url: "<<your-git-repo-url>>", credentialsId: 'git-hub-credentials'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "your-project-name"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
