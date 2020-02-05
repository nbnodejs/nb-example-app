node {
    def app
    stage('CLONE: Clone nb-exampl-app GitHub Repo') {
        checkout scm
    }
    stage('BUILD: Build docker image : nbnodejs/nb-example-app'){
        app = docker.build("nbnodejs/nb-example-app")
    }
    stage('TEST: Run npm test within new nbnodejs/nb-example-app image'){
        app.inside{
            sh 'npm test'
        }
    }
    stage('PUSH: Push built nbnodejs/nb-example-app into Docker hub'){
        docker.withRegistry('https://registry.hub.docker.com','docker-hub-credentials') {
            app.push('latest')
        }
    }
}