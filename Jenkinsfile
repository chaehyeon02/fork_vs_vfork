node {
    def app
    stage('Clone repository') {
        git 'https://github.com/chaehyeon/fork_vs_vfork.git'
    }
    stage('Build image') {
        app = docker.build("lch125/test")
    }
    stage('Test image') {
        app.inside {
            sh 'make test'
        }
    }
    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'lch125') {
           app.push("${env.BUILD_NUMBER}")
           app.push("latest")
        }
    }
}
