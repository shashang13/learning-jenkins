pipeline {
  agent any

  environment {
    ENV_URL='pipeline.google.com'
    SSH_CRED=credentials('SSH')
  }

  stages {

    stage ('One') {
      steps {
        addShortText background: '', borderColor: '', color: '', link: '', text: 'One'
        sh '''
          echo Hello1
          echo Hello2
          echo ENV_URL=${ENV_URL}
        '''
      }
    }
    stage ('two') {
      environment {
        ENV_URL='stage.google.com'
      }
      steps {
//         addShortText background: '', borderColor: '', color: '', link: '', text: 'Two'
        echo "Two"
        sh 'ENV_URL=${ENV_URL}'
        sh 'env'
      }
    }
  }
}