pipeline {
  agent any
  stages {
    stage('syncing files') {
      steps {
        script {
          node
          {
            docker.withRegistry('https://10.1.53.4/','dtr-login'){
              git 'https://github.com/Imransysg/example-voting-app.git/'
              
            }
          }
        }
        
      }
    }
    stage('Building and pushing Vote Image') {
      steps {
        script {
          node
          {
            docker.withRegistry('https://10.1.53.13/','dtr-login'){
              // dtr-login is a login ID in credentials
              git 'https://github.com/Imransysg/example-voting-app.git/'
              def vote_img = docker.build('dockeradmin/voting-app-vote','./vote').push('latest')
              
            }
          }
        }
        
      }
    }
  }
}