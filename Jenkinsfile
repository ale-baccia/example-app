node {
    def app;

    stage('Clone repository') {
        checkout scm //clone the code where the jenkins file is situated and placed in the job work space
    }

    stage('Build image') {
        app = docker.build('06071990/example-app')
    }

    stage('Test image') {
        app.inside {
            sh 'npm test'
        }
    }

    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push('latest')//push the docker image in the registry we are defining
       }
    }
}