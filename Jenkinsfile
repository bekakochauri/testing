
pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t bekakochauri/nginx:latest .'
      }
    }
    stage('Publish') {
      steps {
        script {
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
        sh 'docker push bekakochauri/nginx:latest '
        }
        }
      }
    }

    stage('Deploy') {
      steps {
        input "Are you ready to deploy?"
        sh '''
        cd ~
        ocker stop demo_nginx_1
        docker-compose rm -f 
        docker-compose  up -d
           '''
      }
    }

  }
}

