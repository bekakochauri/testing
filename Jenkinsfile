
pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '/Applications/Docker.app/Contents/Resources/bin/docker build -t bekakochauri/nginx:latest .'
      }
    }
    stage('Publish') {
      steps {
        sh '/Applications/Docker.app/Contents/Resources/bin/docker push bekakochauri/nginx:latest '
      }
    }


    stage('Deploy') {
      steps {
        input "Are you ready to deploy?"
        sh '''
        cd /opt/demo
        /Applications/Docker.app/Contents/Resources/bin/docker stop demo_nginx_1
        /Applications/Docker.app/Contents/Resources/bin/docker-compose/docker-compose rm -f 
        /Applications/Docker.app/Contents/Resources/bin/docker-compose/docker-compose  up -d
           '''
      }
    }

  }
}
