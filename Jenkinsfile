pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'dotnet build eShopOnWeb.sln'
      }
    }

    stage('Test') {
      parallel {
        stage('Unit') {
          steps {
            sh 'dotnet test test/UnitTests'
          }
        }

        stage('Integration') {
          steps {
            sh 'dotnet test test/IntegrationTests'
          }
        }

        stage('Functional') {
          steps {
            sh 'dotnet test test/FunctionalTests'
          }
        }

      }
    }

    stage('Deployment') {
      steps {
        sh 'dotnet publish eShopOnWeb.sln -o'
      }
    }

  }
}