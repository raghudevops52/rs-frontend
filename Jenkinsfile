pipeline {
  agent any

  stages {

    stage('Prepare Artifacts') {
      steps {
        sh '''
          mkdir -p publish
          cp -r static *.conf publish
        '''
      }
    }

    stage('Publish Artifacts') {
      steps {
        sh '''
          cd publish
          az artifacts universal publish --organization https://dev.azure.com/DevOps-Batches/ --project="DevOps52" --scope project --feed devopsb52 --name frontend --description "Frontend" --version 0.0.${BUILD_NUMBER} --path .
        '''
      }
    }

  }
}