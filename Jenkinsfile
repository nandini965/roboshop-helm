pipeline {

  agent any

  parameters {
    string(name: 'component', defaultValue: '', description: 'App Component Name')

  }

  stages {

    stage('Clone App Repo') {
      steps {
        dir('APP') {
          git branch: 'main', url: 'https://github.com/nandini965/${component}'
        }

      }

    }

    stage('Helm Deploy') {
      steps {
        dir('HELM') {
          sh 'helm upgrade -i ${component} . -f ../APP/values.yaml --set app_version=${app_version}'
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