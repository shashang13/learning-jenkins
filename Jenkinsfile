// pipeline {
//   agent any
//
//   environment {
//     ENV_URL='pipeline.google.com'
//     SSH_CRED=credentials('SSH')
//   }
//
//   options {
//     ansiColor('xterm')
//   }
//
// //   triggers {
// //     pollSCM('*/2 * * * *')
// //   }
//
//   tools {
//     maven 'maven-3.8.7'
//   }
//
//   parameters {
//       string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
//       text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
//       booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
//       choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
//       password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
//   }
//
//   stages {
//
//     stage ('One') {
//
//       when {
//         environment name: 'CHOICE', value: 'One'
//       }
//
//       steps {
//         addShortText background: '', borderColor: '', color: '', link: '', text: 'One'
//         sh '''
//           echo Hello1
//           echo Hello2
//           echo ENV_URL=${ENV_URL}
//           mvn --version
//         '''
//       }
//     }
//
//     stage ('two') {
//       environment {
//         ENV_URL='stage.google.com'
//       }
//
//       tools {
//         maven 'maven-3.6.0'
//       }
//
//       when {
//         environment name: 'CHOICE', value: 'Two'
//       }
//
// //       input {
// //         message "Okay to continue?"
// //         ok "Yes"
// //         submitter "alice,bob"
// //         parameters {
// //           string(name: 'Person', defaultValue: 'Shashang Sheth', description: 'Whom shall I say hello to?')
// //         }
// //       }
//
//       steps {
// //         addShortText background: '', borderColor: '', color: '', link: '', text: 'Two'
//         echo "Two"
//         sh 'ENV_URL=${ENV_URL}'
//         sh 'env'
//         sh 'echo -e "\\e[31mHello"'
//         sh 'mvn --version'
//       }
//     }
//   }
// }



pipeline {
//     agent {
//       node { label 'Workstation'}
//     }
    stages {
        stage('Non-Parallel Stage') {
            agent {
                label 'Group1'
            }
            steps {
                echo 'This stage will be executed first.'
            }
        }
        stage('Parallel Stage') {
            failFast true
            parallel {
                stage('Branch A') {
                    steps {
                        echo "On Branch A"
                    }
                }
                stage('Branch B') {
                    steps {
                        echo "On Branch B"
                    }
                }
                stage('Branch C') {
                    stages {
                        stage('Nested 1') {
                            steps {
                                echo "In stage Nested 1 within Branch C"
                            }
                        }
                        stage('Nested 2') {
                            steps {
                                echo "In stage Nested 2 within Branch C"
                            }
                        }
                    }
                }
            }
        }
    }
}