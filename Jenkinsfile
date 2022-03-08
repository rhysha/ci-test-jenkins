node {
    def app
    def DOCKER_HUB_USER = "rhysha"
    stage('Clone repository') {
        checkout scm
    }

    stage('Build image') {
        sh "docker build -t ${JOB_NAME} ."
    }

    stage('Test Image') {
        sh "docker run ${JOB_NAME} --name ${JOB_NAME}"
        sh "docker kill ${JOB_NAME}"
    }

    stage('Tag image') {
        sh "docker tag ${JOB_NAME} ${DOCKER_HUB_USER}/${JOB_NAME}-${BRANCH_NAME}:${env.BUILD_NUMBER}"
    }

    stage('Push image') {
        sh "docker push ${DOCKER_HUB_USER}/${JOB_NAME}-${BRANCH_NAME}:${env.BUILD_NUMBER}"
    }

    stage('Deploy') {
        switch(GIT_BRANCH) {
        case "dev":
            echo "hello dev"
            break
        case "staging":
            echo "hello staging"
            break
        case "master":
            echo "hello master"
            break
        }
    }
}