pipeline {
    agent any

    environment {
        PROJECT_NAME = 'ariiprs-dev'
        BUILD_NAME = 'java-bni-project'
    }

    stages {
      stage('Trigger build in openshift') {
       steps {
         sh "oc start-build ${BUILD_NAME} --from-dir=. --follow -n ${PROJECT_NAME}"}
       }


        stage('Deploy to OpenShift') {
              steps {
                sh "Oc rollout restart deployment/${BUILD_NAME} -n ${PROJECT_NAME}"}
        }
    }


    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build or deployment failed.'
        }
    }
}

// project name dan build name mengikut name dari project masing2