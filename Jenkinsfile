node {
    def app
    stage('Clone repository') {
        checkout scm
    }
    stage('Build image') {
       app = docker.build("jovansimonoski/devops-blueocean-04")
    }
    stage('Push image') {   
        docker.withRegistry('https://registry.hub.docker.com', 'js-dockerhub') {
            app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
            app.push("${env.BRANCH_NAME}-latest")
            // signal the orchestrator that there is a new version
        }
    }
}
