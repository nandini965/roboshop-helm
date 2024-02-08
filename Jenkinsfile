pipeline {
 agent any
parameters {
string(name: 'component', default value: '', description: 'App component')
}
 stages {
  stage('clone APP Repo') {
  steps {
  dir ('APP') {
  git branch : 'main', url: https://github.com/nandini965/${component}.git
  }
  }
  }

  stage('Helm dploy') {
  steps {
  sh 'helm upgrades -i ${component} -f ../APP /values.yaml'
  }
  }
  }
  }
  post {
      always {
        cleanWs()
      }
    }

  }