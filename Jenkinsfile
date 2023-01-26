pipeline {
  agent any

  environment {
    ENV_URL='pipeline.google.com'
    SSH_CRED=credentials('SSH')
  }

  options {
    ansiColor('xterm')
  }

  triggers {
    pollSCM('*/2 * * * *')
  }

  parameters {
      string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
      text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
      booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
      choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
      password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
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
        sh 'echo -e "\\e[31mHello"'
      }
    }
  }
}