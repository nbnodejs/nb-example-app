node {
    def app
    stage('Clone nb-exampl-app GitHub Repo') {
        checkout scm
    }
    stage('Build docker image : nbnodejs/nb-example-app'){
        app = docker.build("nbnodejs/nb-example-app")
    }
    stage('Push built nbnodejs/nb-example-app into Docker hub'){
        docker.withRegistry('https://registry.hub.docker.com','docker-hub-credentials') {
            app.push('latest')
        }
    }
}