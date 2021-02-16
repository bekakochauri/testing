
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
        withDockerRegistry([ credentialsId: "dockerhub", url: "" ]) {

        sh 'docker push bekakochauri/nginx:latest '
        }
        }
      }
    }

    stage('Deploy') {
      steps {
        input "Are you ready to deploy?"
        sh '''
        cd /root
        
        docker stop root_nginx_1
        ls
        docker-compose rm -f 
        docker-compose  up -d
        
           '''
      }
    }

  }
}

