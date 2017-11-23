pipeline {
  agent any
  stages {
    stage('syncing files') {
      steps {
        script {
          node
          {
            docker.withRegistry('https://dtrlb-adockersb.westus.cloudapp.azure.com/','dtr-login'){
              // dtr-login is a login ID in credentials
              git 'https://github.com/Imransysg/example-voting-app.git/'
              
            }
            
          }
        }
        
      }
    }
    stage('Vote Image') {
      parallel {
        stage('Vote Image') {
          steps {
            script {
              node
              {
                docker.withRegistry('https://dtrlb-adockersb.westus.cloudapp.azure.com/','dtr-login')
                {
                  git 'https://github.com/Imransysg/example-voting-app.git/'
                  def vote_img = docker.build('ddcadmin/voting-app-vote','./vote').push('latest')
                }
                
              }
            }
            
          }
        }
        stage('stg') {
          steps {
            script {
              node
              {
                docker.withRegistry('https://dtrlb-adockersb.westus.cloudapp.azure.com/','dtr-login'){
                  // dtr-login is a login ID in credentials
                  
                  git 'https://github.com/Imransysg/example-voting-app.git/'
                  def vote_img = docker.build('ddcadmin/voting-app-vote','./vote').push('latest')
                  
                }
              }
            }
            
          }
        }
      }
    }
    stage('Worker Image') {
      steps {
        script {
          node
          {
            docker.withRegistry('https://dtrlb-adockersb.westus.cloudapp.azure.com/','dtr-login'){
              git 'https://github.com/Imransysg/example-voting-app.git/'
              def worker_img = docker.build('ddcadmin/voting-app-worker','./worker').push('latest')
              
            }
            
          }
        }
        
      }
    }
    stage('Result Image') {
      steps {
        script {
          node
          {
            docker.withRegistry('https://dtrlb-adockersb.westus.cloudapp.azure.com/','dtr-login'){
              // dtr-login is a login ID in credentials
              git 'https://github.com/Imransysg/example-voting-app.git/'
              def result_img = docker.build('ddcadmin/voting-app-result','./result').push('latest')
              
            }
          }
        }
        
      }
    }
  }
}