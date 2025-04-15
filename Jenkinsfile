pipeline {
    agent {
        label "${AGENT}"
    }

    stages {
        stage("Continuous Integration / Intégration Continue") {
            steps {
                git branch: "main", url: "https://github.com/YanisBra/symfony_CICDCD.git"
            }
        }
        stage("Continuous Delivery / Livraison Continue") {
            steps {
                sh "docker build . -t ${DOCKERHUB_USERNAME}/symfony_cicdcd"
                sh "docker login -u ${DOCKERHUB_USERNAME} -p ${DOCKER_PASSWORD}" // Créer un PAT sur Docker Hub : https://app.docker.com/settings/personal-access-tokens
                sh "docker push ${DOCKERHUB_USERNAME}/symfony_cicdcd"
            }
        }
    }
}
