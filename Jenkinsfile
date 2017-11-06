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
  }
}