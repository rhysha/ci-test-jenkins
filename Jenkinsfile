node {
    def app
    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        //app = docker.build("rhysha/hello-jenkins")
        //sh 'newgrp docker'
        sh 'docker build -t hello-jenkins .'
        //docker.build("rhysha/hello-jenkins:0.0.1")
    }

    stage('Test Image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        //app = docker.build("rhysha/hello-jenkins")
        //sh 'newgrp docker'
        sh 'docker build -t hello-jenkins .'
        //docker.build("rhysha/hello-jenkins:0.0.1")
    }

    stage('Tag image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        //app = docker.build("rhysha/hello-jenkins")
        //sh 'newgrp docker'
        sh "docker tag hello-jenkins rhysha/hello-jenkins-${BRANCH_NAME}:${env.BUILD_NUMBER}"
        //docker.build("rhysha/hello-jenkins:0.0.1")
    }

    stage('Push image') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
        sh "docker push rhysha/hello-jenkins-${BRANCH_NAME}:${env.BUILD_NUMBER}"

    }

    stage('Deploy') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
        
    }
}