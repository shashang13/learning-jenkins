pipeline {
  agent any

  stages {

    stage ('One') {
      steps {
        addShortText background: '', borderColor: '', color: '', link: '', text: 'One'
        sh '''
          echo Hello1
          echo Hello2
        '''
      }
    }
    stage ('two') {
      steps {
        echo "Two"
      }
    }
  }
}